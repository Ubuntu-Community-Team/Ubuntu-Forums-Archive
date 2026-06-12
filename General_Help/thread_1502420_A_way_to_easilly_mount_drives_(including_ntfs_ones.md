---
title: "A way to easilly mount drives (including ntfs ones) via gui without password prompt?"
date: 2010-06-05
forum: General Help
---

### Post by Istrebitel on 2010-06-05
Greetings.

I have recently tried to switch from windows to kubuntu. So far nobody can help me on the problem that kubuntu keeps asking password (kdesudo - please input your password to mount this device) in order to mount anything with ntfs on it. This is despite i have made needed changes in order for this operation to be possible without root privilleges (recompiled ntfs-3g with internal fuse, set the setuid bit/setguid bit, added user to disks, gave user permissions to mountpoint). I can do mount /dev/... and it works without sudo but the dolphin, or "removable media" thingie in system settings still will ask a password to mount anything with ntfs on it.
So, therefore a question arises. I can of course do all the mounting manually (automount on boot does not help since my external hard takes time to "boot up" when it's first accessed and that is when system boot takes 10 seconds instead of 1 second and starts complaining about "drive not ready, try manual mounting"... So, i would like to have a simple gui something that can mount or dismount (run mount and umount for me effectively) removable or internal disks. Could someone advise some program that he uses? I suppose there are plenty such around since the operation is very common...
Maybe even a file manager (instead of dolphin)? Preferably one that does renaming like in windows (without popups)?

Thanks in advance!

PS: i am sorry i made a mistake while creating a topic, chosen wrong prefix, dont see how it can be fixed...

---

### Post by cogier on 2010-06-05
Try pysdm. As I don't use Windows any more I can't test it with NTSF drives. In terminal run this ```
sudo apt-get install pysdm
``` then, again in terminal, run ```
sudo pysdm
```. The settings you make become permanent so hopefully that should sort your problem.

---

### Post by Istrebitel on 2010-06-07
Thank you i will try it and write here the result, i hope this is not just a gui to /etc/fstab because if it is it is not going to help me at all...

---

