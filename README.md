# DeployBot API
[![Build Status](https://img.shields.io/travis/JayBizzle/DeployBot-API/master.svg?style=flat-square)](https://travis-ci.org/JayBizzle/DeployBot-API) [![StyleCI](https://styleci.io/repos/40478608/shield)](https://styleci.io/repos/40478608) [![Total Downloads](https://img.shields.io/packagist/dt/JayBizzle/DeployBot-API.svg?style=flat-square)](https://packagist.org/packages/jaybizzle/deploybot-api)
### Installation
Add `"jaybizzle/deploybot-api": "2.*"` to your composer.json.

### Older Versions
If you need to use this with older versions of PHP or Guzzle, then see the `1.0` branch

### Usage
You can read the official DeployBot API documention here - http://deploybot.com/api/

All the DeployBot API endpoints can be called by prefixing the name with `get` e.g

```php
use Jaybizzle\DeployBot;

$db = new DeployBot('YOUR_API_KEY', 'YOUR_ACCOUNT_NAME');

// get all users
$users = $db->getUsers();

// get a specific user
$user = $db->getUsers(324);
```

Some DeployBot API endpoints can accept query string parameters, such as `limit` to limit the number of results returned. Taking the above users example, we can simply do this...

```php
$users = $db->limit(10)->getUsers();
```

These can also be chained...

```php
$users = $db->limit(10)->after(324)->getUsers();
```

Some more examples...

```php
//  list deployments for environment and limit results
$deployments = $db->environmentId(3452)->limit(10)->getDeployments();

// list repositories and limit results
$repositories = $db->limit(20)->getRepositories();
```

_NOTE: Query parameters are listed in the DeployBot API docs as `snake_case` but we access them using `camelCase` methods so all method calls have a consistent naming convention_
