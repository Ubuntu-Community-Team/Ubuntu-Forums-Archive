---
title: "Need HELP! (lost ubuntu from grub)"
date: 2010-02-14
forum: General Help
---

### Post by xdemo on 2010-02-14
```
EDIT: SOLVED
Thanks to louieb for suggesting super grub disk.
1. downloaded http://prdownload.berlios.de/supergrub/sgd_cdrom_1.30.iso
2. burnt to disc using other computer
3. booted the cd, chose automatically search for grub configs
4. my old grub2 appeared listing my ubuntu partition.
```


Hello, first off i cannot access/boot my ubuntu. I am 100% sure the partition is still intact on my HDD as i checked with gparted under Debian.

Basically, i installed Debian Lenny, to a 20gb partition. And the installation went perfect. Except grub (legacy) was installed, thus overwriting my grub2.

I'm having to use my nasty vista partition to write this, as i have not setup netowrking to access the internet in my Debian yet.

All i need to be able to do is, access and boot Ubuntu, so i can type "update-grub", which will hopefully make grub2 the preffered bootloader, listing all of my OS.

My grub2 would display:
```
Ubuntu Karmic 9.10
Memtest +x86
Other OS:
Windows Vista
```And after grub (legacy) has been installed it is only displaying:
```
Debian Lenny
Memtest +x86
Other OS:
Windows Vista
```Can somebody please explain how to re-add ubuntu to the grub. So i can boot into it, and restore grub2.

Any help on how to restore my Ubuntu Karmic partition would be amazing. Thanks!


EDIT:
*UPDATE*
i just browsed past this page: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=511121](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=511121)
Could this be my problem that ext4 filesys are unreadable in grub legacy? I can't fix it though, because there is no network access under Debian and i cannot install grub2 from there.

---

### Post by louieb on 2010-02-14
[Super Grub Disk]("http://linux.softpedia.com/progDownload/Super-Grub-Disk-Download-8071.html")

once you boot Ubuntu you'll need to run grub-install
[IDBS GRUB2 Linux bash Commands]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html") 
[IDBS GRUB 1.97]("http://members.iinet.net/%7Eherman546/p20.html")

---

### Post by xdemo on 2010-02-14
hi, thanks for the reply, i have just booted into my livecd of ubuntu, and went to 
```
/media/blah/usr/bin

(where blah is my partition serial/hash/sid)
```
and ran
```
grub-mkrescue /home/ubuntu/Desktop/grubrescue.iso
```
and burned the iso image to disc, booted into it but could not work out what to do.

Anyway i hope im on the right track, is supergrubdisk a more advanced version of grub-mkrestore?

And what exactly do i need to do. Is it a case of navigating to my menu.lst on the partition i am trying to boot?

Thanks in advance

---

### Post by xdemo on 2010-02-14
Okay i just tried your advice with super grub disk, and used the auto command. But it doesn't do anything but list the same entries as the installed grub. ;(

----------------------
Debian GNU/Linux Kernel 2.6.26-2-amd64
Debian GNU/Linux Kernel 2.6.26-2-amd64 (single user mode)
Other Operating Systems:
Windows Vista/Longhorn (Loader)
----------------------

I've been rebooting my computer alot for the past 3hours now :(
I think the case is that grub (legacy) cannot read ext4 partitions, correct?
As my ubuntu partition i am trying to access is in fact ext4.....

Any more suggestions? as soon as i can boot it, like you said... "grub-install" will overwrite the legacy grub, and list my ubuntu /debian /windows at boot time. I just need to boot it up first. Hmm....

---

### Post by louieb on 2010-02-14
Older versions of Grub legacy can't read ext4. The Grub legacy that comes with Ubuntu since version 9.04 (Jaunty) can read ext4. 

Really surprised Super Grub could not boot Ubuntu.   
Do you have a Ubuntu 9.10 live CD?  You can fix Grub with it.  drs305 has a how to - he has been playing with GRUB2 a lot longer than I. 

[Grub 2 Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1195275")


[LIST=1]
[*]**[COLOR=Navy][SIZE=3]Reinstalling GRUB 2 from LiveCD[/SIZE][/COLOR] **
If you cannot boot from GRUB 2 and need to reinstall it, here is the simple method. For more details or for advanced options, refer to the Ubuntu community documentation here: [Grub2 - Reinstalling GRUB 2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202"):
[LIST]
[*]Boot the 9.10 Karmic LiveCD to the Desktop.
[*]Open a terminal - Applications, Accessories, Terminal.
[*]Determine your normal system partition - `sudo fdisk -l`  (That is a lowercase L)
[*]If you aren't sure, run `df -Th`. Look for the correct disk size and ext3 or ext4 format.
[*]Mount your normal system partition:      Code:
     ```
sudo mount /dev/sdXY /mnt
```
[LIST]
[*]Example: sudo mount /dev/sd*a1* /mnt
[*]Note: The partition to mount is normally the partition on which Ubuntu was installed: sda1, sdb5, etc. If you have a separate /boot partition, use the device on which the /boot partition is located. Grub 2 works best when installed in the MBR of the drive to which BIOS boots. Also remember that you *mount* the partition (including the number) in this step, but you do *not* include the partition number when you run the "sudo grub-install" command later.
[*]Note: GRUB 2 counts the first drive (X) as "0", but the first partition (Y) as "1"
[/LIST]
 
[*]Reinstall GRUB 2:      Code:
     ```
sudo grub-install --root-directory=/mnt /dev/sdX
```
[*]
[LIST]
[*]Example: sudo grub-install --root-directory=/mnt /dev/sd*a*
[*]Note: Substitute the device on which Ubuntu was installed - sda, sdb, etc. Do *not* specify a partition number.
[/LIST]
 
[*]Unmount the partition:       Code:
     ```
sudo umount /mnt
```
[*]Reboot.
[/LIST]
 
[/LIST]

---

