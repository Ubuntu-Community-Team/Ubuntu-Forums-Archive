---
title: "Backintime callback not called any more since Ubuntu Natty 11.04"
date: 2011-04-30
forum: General Help
---

### Post by qnob on 2011-04-30
Hi,

I've installed Ubuntu 11.04 and as a consequence I've installed backintime with new major version > 1.0.

Since the installation (no upgrade), the callback isn't called automatically any more. I've added a log in order to check, if the script is actually called. Negativ! Before the new installation everything worked fine.

```
root@ccc:~/.config/backintime# ls -la
total 16
drwxr-xr-x 2 root root 4096 2011-04-22 13:30 .
drwx------ 6 root root 4096 2011-04-18 19:23 ..
-r--r--r-- 1 root root 2816 2011-04-22 13:06 config
-rwxr--r-- 1 root root  537 2011-04-22 13:30 user.callback
root@ccc:~/.config/backintime# 
```

Anybody as a hint? According to the documentation ([http://backintime.le-web.org/documen/usercallback/](http://backintime.le-web.org/documen/usercallback/) ) there were a few changes in the parameter passing, however, shouldn't prevent backintime to call the callback script. Maybe there is a side effect..

thanks
Kuno

---

