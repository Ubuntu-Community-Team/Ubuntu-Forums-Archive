---
title: "random closures"
date: 2010-05-17
forum: General Help
---

### Post by Swagman on 2010-05-17
I have recently clean installed 10:04 64 bit on new hardware but am getting random closures from various apps

ie:
Firefox
Epiphany
Evolution

Those are the ones that I've actually noticed. 

Does anyone know what's going wrong & how to cure it ?
I've looked through all the logs but most of it is gibberish to me.

---

### Post by lovinglinux on 2010-05-17
Try to uninstall libmoon.

```
sudo apt-get remove libmoon
```

You won't be able to view Silverlight content then, but is better than crashing.

Also make sure you have the the best flash plugin installed according to your system architecture. See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

If that doesn't help (I just noticed that problem occurs with Evolution), then start Firefox from a terminal and post the error output when it crashes.

---

### Post by Swagman on 2010-05-18
Thanks. I'll give that a shot right now

[Edit] It's not installed anyway but it's picked up some other stuff to remove so...

```

paul@pauls-desktop:~$ sudo apt-get remove libmoon
[sudo] password for paul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libmoon is not installed, so not removed
The following packages were automatically installed and are no longer required:
  odbcinst1debian1 odbcinst unixodbc
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
paul@pauls-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  odbcinst odbcinst1debian1 unixodbc
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 1,044kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 168986 files and directories currently installed.)
Removing unixodbc ...
Removing odbcinst1debian1 ...
Removing odbcinst ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
paul@pauls-desktop:~$ 

```

Lets see what happens

---

