---
title: "Gnu Grub version 1.97 Beta4"
date: 2011-02-22
forum: General Help
---

### Post by Rockcarver on 2011-02-22
9.10  installed wubi with XP fails login, leads only to grub terminal (sh:grub>) with blinking cursor. Tab gives a list of possible commands; "boot" gives an error message: no loaded kernel.

I need to somehow get data (pictures) out of the home folder before reloading Ubuntu, maybe a different version.

Any ideas how to retrieve my data before reloading? and any recommendations on which version to replace 9.10 with? and is wubi the best bet? I don't want to dump Windows altogether, because in the present instance, it saved my butt. I use the computer (Asus laptop) for lectures when I teach.  I suspect a bug introduced by recent update of 9.10.

Thanks in advance, folks...

Rockcarver

---

### Post by oldfred on 2011-02-22
Does your windows boot or did the wubi install bug install grub to the MBR?

how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Wubi's most recent versions do have a bug, with fixes posted above. But the purpose of wubi is to give Windows users an easy way to test Ubuntu beyond just a liveCD. They then can easily uninstall since it is only a file inside the NTFS windows partition.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by Rockcarver on 2011-02-22
Wow, Thanks, Oldfred, a lot of things to try! I will go through them and let you know what works. I tried working from the CD, but it generated an empty home file instead of giving me access to my old home file. I hope it did not replace my home file with pictures with an empty one. My main concern, of course, is recovering the data; then I can decide what and how to install.

Rockcarver

---

### Post by Rockcarver on 2011-02-22
Oh, I did not answer your question: Windows boots OK. I am using it now to visit the Forums.

---

### Post by oldfred on 2011-02-22
The liveCD is a Ubuntu system with its own /home. You have to mount or chroot into other systems to see them. Most you can just click with Nautilus the file manager, but I think the only way to get to wubi, is to mount both the windows partition and then the wubi folder loopmounted inside it. Then you should see a full Ubuntu install and have to drill down from filesystem,  /, then home.

---

### Post by Rockcarver on 2011-02-22
OK,    	I am using these instructions which were in one of the links from you: 	 	 	 	 	  
[LIST=1]
[*]In the Ubuntu setup program, 	select the preferred language you use, then select the "Try 	Ubuntu with No Change To My Computer" option.  	
[*]Once at the Ubuntu desktop, in a 	Live session, open up Applications->Accessories>Terminal.  	
[*]Now run:  	
[/LIST]
  [IMG]http://neosmart.net/forums/images/chestnut/misc/code.gif[/IMG]
 [FONT=Consolas, Lucida Console, Courier New, monospace]sudo fdisk -l[/FONT]
[FONT=Consolas, Lucida Console, Courier New, monospace]sudo mkdir /win[/FONT]
[FONT=Consolas, Lucida Console, Courier New, monospace]sudo mount /dev/sdxy /win[/FONT]
[FONT=Consolas, Lucida Console, Courier New, monospace]sudo mkdir /vdisk[/FONT]
[FONT=Consolas, Lucida Console, Courier New, monospace]sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk[/FONT]
         where the "x" and the "y" in "sdxy" is replaced with the correct HDD letter (starting at **a** of course), and the correct partition number (starting at 1), of the Windows partition your Wubi install is on. The first command will have given you the location.
Once running those commands, open up Places>Computer>Filesystem>vdisk, and you should find the contents of your root.disk in there. Now you can backup your data to external media, and reinstall Ubuntu with Wubi if you like.


 sudo fdisk -l  gave this result:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
129 heads, 4 sectors/track, 605778 cylinders
Units = cylinders of 516 * 512 = 264192 bytes
Disk identifier: 0x4592a56d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      198450    51200098    7  HPFS/NTFS
/dev/sda2          198451      605776   105090108    f  W95 Ext'd (LBA)
/dev/sda5          198451      605776   105090106    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS

My attemps at the other commands:

ubuntu@ubuntu:~$ sudo mkdir /win
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /win
ubuntu@ubuntu:~$ sudo mkdir /vdisk
ubuntu@ubuntu:~$ sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
/win/ubuntu/disks/root.disk: No such file or directory
ubuntu@ubuntu:~$ sudo mkdir /win
mkdir: cannot create directory `/win': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /win
mount: special device /dev/sdc1 does not exist
ubuntu@ubuntu:~$ sudo mkdir /vdisk
mkdir: cannot create directory `/vdisk': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /win
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ 

You can guess my thought processes from the choices I made. On the third try at mounting special device I assumed that the C: drive with Windows and the Ubuntu wubi install is a2. If that is correct, how do I specify the file system?

---

### Post by Rockcarver on 2011-02-22
Or is there any way to come at it from the Windows side? I guess Windows can't read Linux files, but could it grab the whole directory and copy to an external drive, then using the Ubuntu CD, extract what I want?

---

### Post by WorMzy on 2011-02-22
sda2 is an extended partition, you won't be able to mount that. Try sda5, but unmount sda1 first. (assuming you're still in the same session)
```
sudo umount /dev/sda1
sudo mount /dev/sda5 /win
```

> mount: special device /dev/sdc1 does not exist

You don't have an sdc, which is why that mount failed. Try sdb1 instead, if sda5 isn't it either.

---

### Post by Rockcarver on 2011-02-22
I think sdb is my external drive, but anyway, I'll give those a shot, thanks.

---

### Post by Rockcarver on 2011-02-22
[B][COLOR=Blue]Here are the next tries. No way to look in sda2? 

[/COLOR][/B][COLOR=Blue][COLOR=Black]ubuntu@ubuntu:~$ sudo mount /dev/sda2 /win
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
/win/ubuntu/disks/root.disk: No such file or directory
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /win
ubuntu@ubuntu:~$ sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
/win/ubuntu/disks/root.disk: No such file or directory
ubuntu@ubuntu:~$ sudo umount /dev/sda1
umount: cannot umount /dev/sda1 -- /dev/sdb1 is mounted over it on the same point.
ubuntu@ubuntu:~$ sudo umount /dev/sdb1
ubuntu@ubuntu:~$ sudo umount /dev/sda1
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /win
ubuntu@ubuntu:~$ sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
/win/ubuntu/disks/root.disk: No such file or directory
ubuntu@ubuntu:~$ sudo umount /dev/sda5
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /win
ubuntu@ubuntu:~$ sudo mount -o loop /win/ubuntu /vdisk
/win/ubuntu: No such file or directory
ubuntu@ubuntu:~$ umount /dev/sdb1
umount: it seems /dev/sdb1 is mounted multiple times
ubuntu@ubuntu:~$ [/COLOR][/COLOR][B][COLOR=Blue][COLOR=Black]

[/COLOR][/COLOR][COLOR=Black][COLOR=Blue]So... what next?[/COLOR]
[/COLOR][/B]

---

### Post by WorMzy on 2011-02-22
> No way to look in sda2?

No, extended partitions are basically just shells which house non-primary partitions, in this case sda5 sits inside it. Since you're getting a 'no such file' error with every partition, I guess you installed Wubi to a non-standard location. Unmount sdb1 (don't forget "sudo" at the start of the umount command) and open re-mount sda1, then run ```
nautilus /win
``` to open the file browser. Take a look around and see if you can find your root.disk, and make a note of it's location, then rerun the mount/loop command with the correct location.

Alternatively, if it's easier for you, just reboot to Windows and check it's location from there.

---

### Post by Rockcarver on 2011-02-22
Yes, I thought I'd look from the Windows side. On the C: drive there is an Ubuntu folder, but it contains only the Install folder, Uninstall folder, Ubuntu logo and boot folder. No Disk folder.

---

### Post by WorMzy on 2011-02-22
That's odd, are you still getting the grub error?

Have you run a disk check recently? Sometimes chkdsk moves root.disk to a "C:\$RECOVERY" folder (or similar), but I've never heard of it moving an entire folder.

Could you have accidentally deleted the disks folder? Check the recycle bin just in case.

You may want to use Windows' search function to see if you can find it that way.

---

### Post by Rockcarver on 2011-02-22
Found it! It had been moved to a "Found" folder along with Swap.disk and Grub.

So maybe I'll just copy it to my external drive and mount it from there with the live cd. Windows probably can't read it, right?

Thanks much for the help!

---

### Post by WorMzy on 2011-02-22
Nah, I don't think Windows can read it. There's (possibly flakey) support for reading ext4 partitions, but I don't think it extends to virtual disks. Rebooting into the LiveCD and refollowing the mount instructions is your best bet.

---

### Post by Rockcarver on 2011-02-22
So I haven't actually seen my pictures yet, but having found the Root.disk, I feel that I can put a Solved tag on the thread.

Thanks again.

---

