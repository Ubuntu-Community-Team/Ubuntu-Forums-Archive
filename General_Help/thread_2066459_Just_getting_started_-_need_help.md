---
title: "Just getting started - need help"
date: 2012-10-04
forum: General Help
---

### Post by decioalex on 2012-10-04
Hi, I have a feel problems happening. Please help.

1. I created two users and whenever I try to switch users, the screen bugs everything, sometimes to the point where I can't see a thing and my only option is to push the reset button. I have a GeForce GT 9500 card.

2. I have two hard disks with 3 partitions other than the one Ubuntu is installed upon. How do I make them visible and usable from the start? Sometimes, it seems the file system can't reconize them and they just won't appear.

3. This is the tougher one. I had a Windows 7 installation and a SuSe Linux installed also. But I wasn't using the SuSe and was thinking on migrating to Ubuntu. Once, while booting into windows the power wen't down and ever since I can't boot through the hard drives anymore. 
My Windows is lost. I managed to install Ubuntu and can run it, but the weird thing is that I can only start Ubuntu if I place a Booting CD on, but choose to boot from HD. If I try to start it or Windows with no CD on, it just keep giving me this error message: "Error, no active partition found".

I ran a GParted distro and found out errors on the windows partition and it recommended I ran chkdsk /f to correct it. But I couldn't make it work through the terminal on Windows intallation disk.
But I just want to correct this so I can boot through the HD. If I can fix this through Linux, so much the better.
What can I do to fix it?

Thanks a lot.
Regards.

---

### Post by Bashing-om on 2012-10-04
decioalex; Hi ! Welcome to the forum .

I'll do what I can to relieve you of some of your tension.

Item 1: Not much I can help with at this time, probably a graphics issue.

item2: fstab (file system table) and the mount command reveals all partitions on your system:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

Item3 is a grub issue:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


Item4: windows tools for windows problems, linux tools for ubuntu situations. You will have to use the window's chkdsk utility to repair windows (or the repair tools either installed or on separate medium). Ubuntu can work with ntfs, but does not have the ability to fix ntfs . Then it is GParted's turn to reclaim the old os disk space usage.

I would suggest that fixing windows errors is the first priority, all the rest is just reading for comprehension to edit a couple or three config files. Nothing much to it ONCE you know what is going on. 

When you are prepared to proceed, we are here and will assist in any way. In this future, one item per post to avoid confusion and as an aid to others seeking solutions.
[INDENT]kindest regards <==BDQ

[/INDENT]

---

### Post by decioalex on 2012-10-05
Hi, thanks for the help and for the welcome :)

1. This morning after seeing your message, I wen't back to update the drivers and turns out the driver never got updated (although it started to yesterday). Maybe there was some connections issues. Since I had to run to work, I haven't been able to test it but will.

2. This morning, all the hard drives were automatically mounted correctly by the system. So maybe this was a problem that only happened right after the instalation? Or maybe it is intermitent? I will check on this later tonight and if the problem persists, I will be sure to follow the links you posted. Thanks!

3. I was concentrating on trying to solve the windows problem, last night, as you suggested. But nothing seemed to work. Chkdsk, formating the old windows partition and trying a new install, the fixmbr and fixboot terminal commands, nothing. It still keeps saying "Error, no active partition", but works once I boot to a CD, but tell the system to boot through the harddisk. I am lost on what else I can do, specially since this is a new HD which was doing quite well, before the problem.

Again, thanks for all the help, BDQ

---

### Post by Bashing-om on 2012-10-05
You are welcome; We are all in this together and I do what little I can to promote ubuntu.

On the windows booting issue - I have not touched windows in years- but, sounds like a boot loader issue (windows has  boot instruction code too !). You can google windows bootloader and see what results.

[INDENT]give us a shout if there is aught else we can do <==BDQ

[/INDENT]

---

### Post by decioalex on 2012-10-09
Hi, BDQ.

I've followed the instructions and built my fstab as follows:


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f657238e-221f-42f4-9a12-72541ec8fa5c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=decf5214-0bf1-4a69-ab9d-94daa6413be8 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/sda1 /media/Windows ntfs-3g defaults,locale=pt_BR.utf8 0 0
/dev/sda2 /media/Dados ntfs-3g defaults,locale=pt_BR.utf8 0 0


This works fine whenever I use mount -a on the terminal. But whenever I boot the system either the 2 windows partitions are not correctly recognized, or they are mounted but without the labels I used (both have the same size and gets mounted as "File System", so it is confusing).
How can I make it mount the HDs as I specified on the fstab every time I start the system?

For the other problems, the video problem is not 100% resolved but it's better now with the updated driver. And the windows boot problem finally is resolved. Turns out, for some reason, the computer was looking for the booting partition on the wrong HD, and since it couldn't find it, instead of looking on another one it just hang. :)

Thanks and regards
Decio
Decio

---

