---
title: "Second Drive Issues 12.04"
date: 2012-08-20
forum: General Help
---

### Post by SOLS on 2012-08-20
I just built a PC and installed a small ssd for the OS and a mechanical hard drive, a Seagate, for saving files etc. on.  I followed the guide at found at [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) and chose to mount Manually as the last step.  However I am unable, when the Seagate is mounted in /media/seagate to write to the disk.  I am not sure what I need to change.  Here is what my etc/fstab shows

<file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ce07a209-2fc6-45ba-874f-55feb2ce4e63 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c9db18c8-8f5f-4be6-b6ed-3a696ccbbc18 none            swap    sw              0       0

I have read a bit about needing to change something here, I just don't know what.  I formatted the disk FAT32 if that helps.  Cheers!

---

### Post by oldfred on 2012-08-20
I would not use FAT32 unless drive is very small. You cannot store any file over 4GB and it does not have a journal, so repairs take longer and on a large drive very long.

from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2
** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a

More info if desired:
Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

