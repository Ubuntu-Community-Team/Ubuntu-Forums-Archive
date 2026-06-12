---
title: "fstab file permissions for external ntfs drive"
date: 2011-08-16
forum: General Help
---

### Post by doogiekd on 2011-08-16
dear friends, 

i have tried everything i could think of:

i am trying to have an external ntfs 1tb hard drive allow read write and execute permissions to all files and folders.

i have used ntfs-3g, pysdm, and mount manager.

ntfs-3g does not allow me to change to the desired permissions because it checks (and does not allow me to unceck) the "apply to internal hard drive" box when i do so, which breaks the computer and does not allow it to boot.

i even tried editing fstab to:

proc                                       /proc           proc  nodev,noexec,nosuid                   0  0  
UUID=f8707dff-cdca-47ad-bc5b-9c73e677ba1a  /               ext4  errors=remount-ro                     0  1  
UUID=EEAC21F1AC21B4CD                      /media/sdb1     ntfs  defaults,gid=1000,uid=1000,umask=000  0  0  
UUID=0ab46b8f-6359-4b27-82c8-b8d279669160  none            swap  sw                                    0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8              0  0  

(this is the current fstab setting)

sdb1 is the external had drive.

also, i tied changing the permissions of /media/sdb1 (mount point) but it does not help. i cannot change any of the folders to have read, write & execute permissions for all users. when trying to change a specific folder permission on sdb1, the drop down menu does not allow me to change to read and write permission, and the menu "retuns" to blank.

any suggestions?

---

