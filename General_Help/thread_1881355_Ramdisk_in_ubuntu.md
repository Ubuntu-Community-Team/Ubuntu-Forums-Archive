---
title: "Ramdisk in ubuntu"
date: 2011-11-15
forum: General Help
---

### Post by caka2604 on 2011-11-15
I want to make ubuntu that will reset everything user working after reboot. The idea is : backup some directories as: home, var, tmp... in a different location and then create a folder with the same name and mount them to ram , when booting, the machine will perform copy data in backup to the folder mounted on the ram. 
Specifically, do the following with my home directory: 
1. create folder homebackup 
2. boot from livecd to copy data on /home  to /homebackup 
3.create a home directory on the ram by adding to /etc/fstab: **tmpfs / home tmpfs defaults, size = 100 0 0** 
4. create a script file "abc" in init.d the command "cp Rf /homebackup/* /home. Then: update-rc.d/etc/init.d/abc defaults 
5.reset 
The result: data from /homebackup are copied to /home but when i reboot appear the following error message: 
- **Could not update file ICEauthority / home/n2m/.ICEauthority **
-** There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)**

Do the same with /var directory: os not runing on GUI, only command-line operations 
Can anybody explain my problem? :(

---

