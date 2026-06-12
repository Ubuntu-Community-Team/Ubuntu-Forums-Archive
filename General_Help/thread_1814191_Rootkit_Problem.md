---
title: "Rootkit Problem?"
date: 2011-07-29
forum: General Help
---

### Post by auwally on 2011-07-29
I have just completed a rkhunter check of my system and it come up with two warnings: usr/bib/bsd - mailx and usr/bin/mail.  I have very basic knowledge of linux but figure it is pointing to email system - is this of concern / a known problem or a 'false' positive. Any advice much appreciated.

Thanks.

---

### Post by mikewhatever on 2011-07-29
You should check the log and see what the warnings actually say, then you can decide if it's worth your attention or not.

---

### Post by yetiman64 on 2011-07-29
As mikewhatever notes you should read the file /var/log/rkhunter.log to check what the warning is about. 

Generally I find entries in the first section of rkhunter (the file properties) give regular warnings as a result of even updating the system, a file is changed by the update and rkhunter detects the different (newer) file and gives a warning. To let rkhunter know of updated files the command ```
sudo rkhunter --propupd
``` is used, then run rkhunter again and all should show as clear. I personally take warnings further down the results far more seriously than the file properties section.

Ideally to know if an update is causing the changes, you should run rkhunter before each update then again after the update and if a warning occurs it is safe to update the file properties in rkhunter (that is quite a lot of work though ;)).
[B]
Edit[/B]: the file permissions on rkhunter.log are very restrictive, to read it use the code in terminal,```
gksu gedit /var/log/rkhunter.log
```as it can't be opened as a normal user.

---

### Post by auwally on 2011-07-29
Thanks Mikewhatever and Yetiman64 (excellent detail).  Checked file and advising was files exist on system but is not present in the rkhunter.dat file.  While in file found this info:

Performing filesystem checks
[17:04:15] Info: Starting test name 'filesystem'
[17:04:15] Info: SCAN_MODE_DEV set to 'THOROUGH'
[17:04:17]   Checking /dev for suspicious file types         [ Warning ]
[17:04:17] Warning: Suspicious file types found in /dev:
[17:04:17]          /dev/shm/pulse-shm-1059276290: data
[17:04:17]          /dev/shm/pulse-shm-1031846872: data
[17:04:17]          /dev/shm/pulse-shm-831195261: data
[17:04:17]          /dev/shm/pulse-shm-2374959818: data
[17:04:17]          /dev/shm/pulse-shm-809057355: data
[17:04:17]          /dev/shm/pulse-shm-1095231782: data
[17:04:18]   Checking for hidden files and directories       [ Warning ]
[17:04:18] Warning: Hidden directory found: /etc/.java
[17:04:18] Warning: Hidden directory found: /dev/.udev
[17:04:18] Warning: Hidden directory found: /dev/.initramfs

Am I digging a deeper hole?

---

### Post by gandaran on 2011-07-29
> **auwally said:**
> Thanks Mikewhatever and Yetiman64 (excellent detail).  Checked file and advising was files exist on system but is not present in the rkhunter.dat file.  While in file found this info:

Performing filesystem checks
[17:04:15] Info: Starting test name 'filesystem'
[17:04:15] Info: SCAN_MODE_DEV set to 'THOROUGH'
[17:04:17]   Checking /dev for suspicious file types         [ Warning ]
[17:04:17] Warning: Suspicious file types found in /dev:
[17:04:17]          /dev/shm/pulse-shm-1059276290: data
[17:04:17]          /dev/shm/pulse-shm-1031846872: data
[17:04:17]          /dev/shm/pulse-shm-831195261: data
[17:04:17]          /dev/shm/pulse-shm-2374959818: data
[17:04:17]          /dev/shm/pulse-shm-809057355: data
[17:04:17]          /dev/shm/pulse-shm-1095231782: data
[17:04:18]   Checking for hidden files and directories       [ Warning ]
[17:04:18] Warning: Hidden directory found: /etc/.java
[17:04:18] Warning: Hidden directory found: /dev/.udev
[17:04:18] Warning: Hidden directory found: /dev/.initramfs

Am I digging a deeper hole?
they are just warnings, nothing wrong there, if you don't want to see the warnings again you can edit the rkhunter configuration file and uncomment the corresponding warning options
```
gksu gedit /etc/rkhunter.conf
```

---

### Post by yetiman64 on 2011-07-29
> **auwally said:**
> ...
Am I digging a deeper hole?

No. As gandarin notes they are just minor warnings that can be gotten rid of by altering the rkhunter.conf file (a normal part of setting up rkhunter for me).

Open /etc/rkhunter.conf with gedit,
```
gksu gedit /etc/rkhunter.conf
``` use the search box to quickly find the different sections ALLOWDEVFILE and ALLOWHIDDENDIR.

Under the ALLOWDEVFILE section add in the line,
> ALLOWDEVFILE=/dev/shm/pulse-shm-* this one entry will account for all the pulse warnings.

Under the ALLOWDEVFILE section add in the lines,

> ALLOWHIDDENDIR=/etc/.java
ALLOWHIDDENDIR=/dev/.udev
ALLOWHIDDENDIR=/dev/.initramfsOnce you save the rkhunter.conf file you should now be able to get a clean result on the next run and if an infection occurs it will be far more obvious to you with a well set up rkhunter install.

---

### Post by auwally on 2011-07-29
Gentlemen thank you all.  Yetiman64 the best to all you 'banana benders'.

---

