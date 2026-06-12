---
title: "Newbie's dd problem"
date: 2012-04-16
forum: General Help
---

### Post by chenxinghao on 2012-04-16
I installed Ubuntu 11.10 (with the install CD disk) on to my Thinkpad X41 Tablet laptop a little more than a week ago on an 8GB USB thumb drive. This USB drive was quickly occupied over by a few applications I installed from the Software Center, with less than 2GB space left.
 
This past weekend I bought a 16GB USB thumb drive (Sandisk Cruzer Fit, with low profile) and used the dd command to "clone" the 8GB on to this new 16GB drive. 
 
Well, it took a little more than 2 hours for 
 
sudo dd if=/dev/sda1 of=dev/sdb1
 
to complete. But the problem is that the resulting 16GB USB thumb drive doesn't boot!
 
Any advice is very much appreciated.

---

### Post by mabo5184 on 2012-04-16
Hi, 
 
I'm a newbie as well but I think I would use gparted to view the new thumbdrive partition to check that the boot flag is set ...

---

### Post by iponeverything on 2012-04-16
```
sudo dd if=/dev/sda1 of=dev/sdb1
```


should be

```
sudo dd if=/dev/sda1 of=/dev/sdb1
```

though that may not be your issue. As for taking a long time to complete that is not surprising -- I also think that "cloning" bootable usb drives via dd is problematic -- though I have never tested it myself.

---

### Post by oldfred on 2012-04-17
You only cloned the partition, but the MBR is used for booting and maybe partition table. You cannot clone partition table anyway as new drive is twice as large.

You may just need to install grub2's boot loader to the MBR if a full install, or syslinux if a liveCD type install.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Or manually reinstall grub2's boot loader to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by chenxinghao on 2012-04-17
Thanks for all the replies. 
 
I posted a note (about moving my Ubuntu installation from 8GB USB stick to a 16GB one) on this forum last week and someone suggested using dd and gave the command line syntext. But when I searched on this forum with my ID chenxinghao it doesn't show up in the search results. This led me to this second post.
 
The missing / in the line syntext was my typo in the post, not in the run.
 
The suggestions related to MBR repairs sound complicated to me and I am not comfortable to pursu it for now. The Ubuntu installation is so simple and straight forward that I may just do a fresh install on the 16GB stick.
 
When I moved the original Windows XP Pro installation on my desktop PC from a 60GB HDD to a Western Digital 300GB unit I downloaded a disk cloning software from the manufacture's site. After running the application, I moved the 300GB HDD into the master slot and the PC booted without any problem. The process was simple, as it should be.
 
Perhaps a similar simple-and-straightforward Ubuntu disk cloning utility or a process (no tweaks) is needed.

---

