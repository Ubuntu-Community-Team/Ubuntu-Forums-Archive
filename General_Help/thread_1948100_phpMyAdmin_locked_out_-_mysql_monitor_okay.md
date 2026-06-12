---
title: "phpMyAdmin locked out - mysql monitor okay"
date: 2012-03-27
forum: General Help
---

### Post by airper on 2012-03-27
Hey Guys,

Looking for a little bit of help, I've managed to lock myself out of phpMyAdmin somehow, playing around with Privileges.

System is standard, 11.10 with php 5.3 and phpMyAdmin 3.4. 

So I was adjusting the Privileges for local and global access rights to specific databases. All seems okay, no SQL errors reported. I shut phpMyAdmin down and then couldn't get back in with my root login and password.

I've checked using mysql monitor and the login and password are intact and I can list all the databases in the CLI, but if I try and log into phpMyAdmin I get  this reported and no access. 

**'Cannot start session without errors, please check errors given in your  PHP and/or webserver log file and configure your PHP installation  properly.'**

The root login and password are definitely okay using mysql monitor on the CLI. 

So I tried to reinstall phpMyAdmin, but same result. I guess I've messed up a config file somewhere, but I can't seem to find anything to help so far. Anyone got any ideas how I can fix this?

I've Googled and search here on the forums, but couldn't find anything specific to the situation I'm in.

Glad of any help, or pointing in the right direction.

Thanks

Wayne

---

### Post by airper on 2012-03-28
Okay the fix is very simple so here it is for anyone else looking at this or similar problems.

Session management in phpMyAdmin is a bit buggy and causes all kinds of spurious issues. 

It seems if you get a red warning banner and this message then you have a session issue

**'Cannot start session without errors, please check errors given in  your  PHP and/or webserver log file and configure your PHP installation   properly.'**

It fix is very simple, just clear down the browsers history and cache files. It will clean up the session and you will be able to log in again.

This is pretty common knowledge, but I hadn't related my playing around with Privileges in some databases, with this issue, having logged out cleanly. 

Simple hey.

---

