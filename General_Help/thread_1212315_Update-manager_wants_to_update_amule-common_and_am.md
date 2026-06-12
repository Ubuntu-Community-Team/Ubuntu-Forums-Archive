---
title: "Update-manager wants to update amule-common and amule-daemon"
date: 2009-07-13
forum: General Help
---

### Post by InkyDinky on 2009-07-13
Update-manager wants me to update amule-common and amule-daemon and yet I don't have amule installed at all.  Do I *really* need to update these packages?   
```
nicolae@nicolae-desktop:~/Desktop$ sudo apt-get remove amule
[sudo] password for nicolae: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package amule is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.

```
I'm pretty sure that I had amule on my system at one point but have since removed it.
Are these packages used by something else on my system? How do I find out?
I can't imagine that the update-manager isn't smart enough to know that amule was removed.
Thanks in advance,
Nick

---

### Post by ibutho on 2009-07-13
If you do not have amule installed anymore, just uninstall the amule-common and amule-daemon packages if you do not need them.

---

### Post by InkyDinky on 2009-07-13
Cool. Thanks!

```
nicolae@nicolae-desktop:~/$ sudo apt-get remove amule*
[sudo] password for nicolae: 
Sorry, try again.
[sudo] password for nicolae: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting amule-adunanza-utils-gui for regex 'amule*'
Note, selecting amule for regex 'amule*'
Note, selecting amule-utils-gui for regex 'amule*'
Note, selecting amule-gnome-support for regex 'amule*'
Note, selecting amule-utils for regex 'amule*'
Note, selecting amule-daemon for regex 'amule*'
Note, selecting amule-adunanza for regex 'amule*'
Note, selecting amule-common for regex 'amule*'
Note, selecting amule-emc for regex 'amule*'
Note, selecting amule-adunanza-daemon for regex 'amule*'
Note, selecting amule-adunanza-utils for regex 'amule*'
The following packages were automatically installed and are no longer required:
  libupnp3 libcrypto++7
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  amule-common amule-daemon
0 upgraded, 0 newly installed, 2 to remove and 2 not upgraded.
After this operation, 9626kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 255810 files and directories currently installed.)
Removing amule-daemon ...
 * Not starting aMule daemon, AMULED_USER not set in /etc/default/amule-daemon.
Removing amule-common ...
Processing triggers for man-db ...
nicolae@nicolae-desktop:~/$ sudo apt-get autoremove 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libupnp3 libcrypto++7
The following packages will be REMOVED:
  libcrypto++7 libupnp3
0 upgraded, 0 newly installed, 2 to remove and 2 not upgraded.
After this operation, 4436kB disk space will be freed.
Do you want to continue [Y/n]? 

```

---

