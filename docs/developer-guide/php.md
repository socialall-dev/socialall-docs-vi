## Installation

Clone with git

[https://github.com/sandklock/soclall-api-php](https://github.com/sandklock/soclall-api-php)

```
<?php
// Register app id and secret key
$soclall = new SoclAll('app_id', 'secret_key');
?>
```

## Authentication

Let user login and authenticate with your application.

```
<?php
// Get login url
$login_url = $soclall->getLoginUrl('network', 'callback_url');
// Redirect user to login url
header('Location: '.$login_url);
?>
```

## API

### /user

This endpoint retrieves user information.

```
<?php
// Get user object
$user = $soclall->getUser('token');
?>
```

The `result` returns [`user`](user-object.md) JSON object structured like this:

```
{
  // general
  "id": 2,
  "username": "Boy",
  "email": "boy@socialall.io",
  // name
  "full_name": "Boy Nguyen", // full name || first name + lastname
  ...
}
```

### /friends

This endpoint retrieves user's friends.

```
<?php
// Get friend list
$friends = $soclall->getFriends('token');
?>
```

The `result` returns an array of [`user`](user-object.md) object like this:

```
[
  {
    "id": 2,
    "username": "Boy",
    "email": "boy@socialall.io",
    ...
  },
  {
    "id": 3,
    "username": "Girl",
    "email": "girl@socialall.io",
    ...
  }
]
```

### /message

This endpoint will send `message` to user's friends.

```
<?php
// Send a message to friends
$soclall->sendMessage('token', 'message', $friend_ids, $title = '');
?>
```

### /publish

This endpoint will publish a message to user's wall/timeline/stream.

```
<?php
// Publish a message to wall/timeline/stream
$soclall->publish('token', 'message');
?>
```

The `result` returns a JSON object structured like this:
```
{
    "link": "https://www.facebook.com/.../posts/..."
}
```
