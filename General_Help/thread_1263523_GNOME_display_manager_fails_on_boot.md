---
title: "GNOME display manager fails on boot"
date: 2009-09-11
forum: General Help
---

### Post by abccbaabc0 on 2009-09-11
Hi. Yesterday I was prompted to update several packages by update manager, around 54Mb in all. Among the updates were updates for firefox and GNOME. The packages downloaded fine, but as they were being implemented, I recieved a lot of messages telling me that the installation had failed, including one that told me the system had recovered from a crash. 
 
I closed the update manager, but I could no longer open any application. I restarted the machine. Upon rebooting I was not given the normal login screen, but a command line version, the same as the terminal prompt. No error messages. I restarted and chose 'recovery mode'. Once the computer had booted I chose 'resume normal boot'. On the list of tasks the computer did, all read [OK] except GNOME display manager, which failed.
 
 
I have tried dpkg. This gave errors along the lines of:
'apt problems prevent configuration of gnome-terminal however gnome-terminal is not configured yet
gnome-terminal data (>=2.26) dependancy errors
dpkg: error processing gnome-terminal (--configure)'
 
similar errors were given for firefox and GNOME terminal-data.
 
 
I have also tried using aptitude. Just pressed 'g' twice. 
'Failed htpp://gb.archive.ubuntu.com jaunty-updates/main brasero 2.26.1'
This was repeated for all the different updates, then
'could not download'
'update aborted'
and 'restoring original system state'
 
I have tried booting into an older kernel version also. No difference.
 
Any help as to what I should do from here would be appreciated. I'm still an ubuntu amateur, so please clearly explain what I should do. : )
Thanks.

---

### Post by P4man on 2009-09-11
Is it possible your partition is full? From a terminal, type 

```
df -h
```

Check if your partitions, especially the root "/" partition isnt full.

If its not full, then reboot in recovery mode, select a root shell, and try this:

```
dpkg –configure -a
```

---

### Post by abccbaabc0 on 2009-09-11
No, none of the partitions are full to more than 80%
 
Typin dpkg --configure -a gives the same errors as before:
'dependancy problems prevent configuration'
with gnome, xulrunner and firefox.

---

### Post by abccbaabc0 on 2009-09-11
bump

---

