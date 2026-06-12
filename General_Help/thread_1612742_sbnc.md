---
title: "sbnc"
date: 2010-11-03
forum: General Help
---

### Post by Corex on 2010-11-03
Hello, i have Ubuntu 10.04 and installed sbnc, now i'm trying to start it, i type sbnc and get:
```
shroudBNC (loader: 1.2 $Revision: 1080 $) - an object-oriented IRC bouncer
Daemonizing... DONE
```
 
But there's no process,
i type "sbnc --foreground" and i get
```
shroudBNC (loader: 1.2 $Revision: 1080 $) - an object-oriented IRC bouncer
Please use absolute path for starting sbnc.
```
 
and if i run "/usr/sbin/sbnc --foreground" i get:
```
shroudBNC (loader: 1.2 $Revision: 1080 $) - an object-oriented IRC bouncer
No valid configuration file has been found. A basic
configuration file can be created for you automatically. Please
answer the following questions:
1. Which port should the bouncer listen on (valid ports are in the range 1025 - 65535): 6667
2. What should the first user's name be? admin
Please note that passwords will not be echoed while you type them.
3. Please enter a password for the first user:
4. Please confirm your password by typing it again:
 
```
But still no process. (same msg if i run the same again, also with a user that doesn't have "wheel" group or access to root stuff.
 
 
 
Anyone know how to get this started?

---

### Post by Corex on 2010-11-04
Nvm, i removed the package, seemed like it didn't wanna save the config, i installed from source instead and i got the "saved conf file" msg and now it works.. Thx anyways.

---

