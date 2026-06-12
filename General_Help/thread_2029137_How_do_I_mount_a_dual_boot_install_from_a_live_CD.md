---
title: "How do I mount a dual boot install from a live CD?"
date: 2012-07-19
forum: General Help
---

### Post by DrReaper on 2012-07-19
My friend decided to upgrade to 12.04 without a backup. 12.04 is not loading now. I can get to a Ctrl+Alt+F1 terminal but for some reason it refuses our username. 

Anyway I want to try to mount the install from a live CD so I can try to load a newer video driver, or even backup his files. Does anyone know what steps it takes to mount the dual boot ubuntu install? sda1 is the windows install and sda2 is the windows recovery partition. We are dual booting windows xp and ubuntu. If I try to mount sda3 or sda4 it says they don't exist.

---

### Post by oldfred on 2012-07-19
Windows will not show the Linux partitions. But you can use the liveCD or USB that you used to install. LIveCD has no password, just hit enter.

In Nautilus you should then be able to see all the partitions on the hard drive.

But if you want to install into the system, you have to chroot into it.

drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

If a boot issue this may help. And you can post the details (link from BootInfo) so we can make specific recommendations:

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

