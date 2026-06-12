---
title: "Run script as a user on startup (before login)"
date: 2010-05-21
forum: General Help
---

### Post by XCan on 2010-05-21
I am wondering how to run a script on startup as a given user before logging in. I know that one can somehow edit /etc/rc*.d, or use the update-rc.d utility. But is a bit unclear to me how to specify the user the script should be run under.

---

### Post by yota on 2010-05-21
extract from "man su"
```


NAME
       su - change user ID or become superuser

SYNOPSIS
       su [options] [username]

DESCRIPTION
       The su command is used to become another user during a login session. Invoked without a username, su defaults to becoming the superuser. The
       optional argument - may be used to provide an environment similar to what the user would expect had the user logged in directly.

```

So for instance to launch che command "ls" as user "john" you would do a:
```

su john -c ls

```
if you launch it as root no password will be requested, otherwise you'll have to enter john's password.

This is just a way, but have also a look at "sudo" or consider to launch the script as a part of the user session... What solution is the best one depends on your specific needs.

Hope this helps!

---

