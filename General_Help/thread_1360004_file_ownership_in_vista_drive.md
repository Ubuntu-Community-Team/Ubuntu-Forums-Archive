---
title: "file ownership in vista drive"
date: 2009-12-20
forum: General Help
---

### Post by sn0m on 2009-12-20
Hi guys
I have a vista partition in my linux drive where pda files are kept. (it is frustrating but i cannot get it to synchronise with win xp in VB machine).
Anyway i like to be able to edit this files with open office word processor (i don't normally boot vista unless I need to synchronise files.)
However, if i open one of them, i get a box that file is locked by unknown user for editing and I can only open a read only copy.
Does any of you know a work around with this. I didn't have any problems before with win xp before, but hey, the new laptop has vista only drivers-so microsoft like behaviour.
Anyway, thanks for your help in advance

Sokol

---

### Post by oldfred on 2009-12-20
How are you mounting the windows partiiton. I think the new auto mount does not give as many permissions as before, but I mount in fstab and have no issues. My original fstab entry from 9.04 made every .txt executable but my current entry just works. 

# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager

---

### Post by MaindotC on 2009-12-20
> **sn0m said:**
> Hi guys
I have a vista partition in my linux drive where pda files are kept. (it is frustrating but i cannot get it to synchronise with win xp in VB machine).

This is most likely due to a driver conflict.  When you connect your pda, Ubuntu is loading a driver to interact with the device (maybe rndis_host) and that conflicts w/ Vbox trying to communicate with it.  You need to see what driver is being loaded and blacklist it.

---

