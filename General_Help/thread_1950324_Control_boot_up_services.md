---
title: "Control boot up services ?"
date: 2012-03-31
forum: General Help
---

### Post by wlouis on 2012-03-31
How can I control what services are run when booting the system ? also I am using kexec and noticed several services are not loaded when I run kexec, how can I control those services as well ?

In other words: how can I control regular boot up services and kexec boot up services ?

Please advice,

---

### Post by electrojustin on 2012-03-31
I don't know much about kexec, but regular bootup services are controlled by startup scripts and some config files in /etc/init. If you want to add a script to run on bootup. Write a script and put it in /etc/init.d. Then use update-rc.d. For example, if you wanted to add script foo to every runlevel:
 
```
 update-rc.d foo default
```
 
If you want to remove a script, go to the directory of the runlevel you want to remove it from (the default is /etc/rc2.d) and change the name of the script from SXfoo to KXfoo where X is some 2 digit number that prefaces the name of the script (update-rc.d automatically generates this number I believe). Alternatively, if you want to remove a script foo completely:
 
```
update-rc.d -f foo remove
```
 
If its an actual service you want and not a script, look at the Upstart config files in /etc/init.
 
It might help to list exactly what you are trying to control

---

