---
title: "Ubuntu newbie Portege success / permissions problem"
date: 2006-03-08
forum: General Help
---

### Post by Delboy2 on 2006-03-08
First of all, can I just report what a complete doddle it was to install this distro.  Having an exernal pcmcia cdrom has meant many hours trying to boot other .isos which all boot up fine and then hang when they " can't find base files or data etc.".  The boot sequence loses sight of it's own location so to speak and is lost after that.  Ubuntu is the first distro I have tried on this machine which keeps sight of the cdrom and loads the base files without a hitch.  (Some other distros boot when a duplicate set of .iso files are copied to my hard disk hda1 first which are then found as a substitute)  Anyway Ubuntu has this problem cracked.  Everything, including the tricky savage S3 video card was detected and configured properly.  Very impressive.
My problem is that, having tried U5.04 a while ago in which drives/partitions were not automounted, I was looking forward to having this facility in 5.10.
It works - my hda 1, cd-rom, hda4 are all displayed  and I can view the contents from Nautilus.  What I cannot do is change permissions for the hda1 Dos/Win partition so that I can copy files back and forth to my Ubuntu partition.  I have done a sudo -su change to be root and also followed the mounting command instructions in 'Help' but no luck.  Everthing seems to be mounted but I am not allowed to copy to/from hda1.  
How do I go about gaining write access to this partition from Ubuntu please?

---

### Post by mättu on 2006-03-08
[http://www.ubuntuforums.org/showthread.php?t=139383&highlight=mount+fat+32](http://www.ubuntuforums.org/showthread.php?t=139383&highlight=mount+fat+32)

hope this helps.
:m)

---

### Post by Zimmer on 2006-03-08
Hello.
HAve a look here 
[http://ubuntuforums.org/showthread.php?t=134389&highlight=fat32+win](http://ubuntuforums.org/showthread.php?t=134389&highlight=fat32+win)
[http://ubuntuforums.org/showthread.php?t=138203&highlight=fat32+win](http://ubuntuforums.org/showthread.php?t=138203&highlight=fat32+win)
and 
[https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)
read particularly with regard to NTFS file systems.
It would appear that people who want to swap files between Ubuntu and Windows on a dual boot system create a separate FAT32 partition as a swap area...
Hope this is of help..
Regards

---

### Post by Delboy2 on 2006-03-08
Wow - that was quick!  Thanks.  I believe the mounting of my hda1 vfat partition is not the issue - I can see everything in it from Nautilus.  The permission change from read only to write is what I am having a problem with.  After I sudo -su changed to root, the right click, 'properties/permissions' list still staed that I was 'not the owner' and therefore could not change permissions. 
Will it help I reboot in recovery mode and log in as root?  What is the root password by the way?  I must have missed it somewhere.

---

### Post by Delboy2 on 2006-03-08
Just got home and tried rebooting to Ubuntu 'recovery' option from Grub.  I typed "startx" at the 'root'/ prompt and, then was able to copy to and delete files within hda1 (Dos/win).  Thats all.

---

