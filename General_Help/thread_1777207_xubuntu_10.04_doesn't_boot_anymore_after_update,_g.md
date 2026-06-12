---
title: "xubuntu 10.04 doesn't boot anymore after update, grub problems."
date: 2011-06-07
forum: General Help
---

### Post by Randy_Rhoads on 2011-06-07
Hello everybody, I am new to the forum and not an expert linux user.
After a recent update (didn't see what kind of update beacuse wasn't me at the pc) the system doesn't boot and gives the fololopwing error:

```
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target file system doesn't have /sbin/init.
No init found. Try passing init=bootarg.
```With the livecd I type in a terminal ```
 sudo fdisk -l 
``` and I get:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009ac3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60431   485407744   83  Linux
/dev/sda2           60431       60802     2976769    5  Extended
/dev/sda5           60431       60802     2976768   82  Linux swap / Solaris, 
```sda2 and sda5 have the same start/end, is it normal?
I tried to mount sda1 with:
```
sudo mkdir /mnt/oldxubuntu
sudo mount /dev/sda1  /mnt/oldxubuntu
``` but nothing happens.
Any suggestion? Thank u. :D

---

### Post by pqwoerituytrueiwoq on 2011-06-07
sda2 and sda5 have the same start/end, is it normal?
for a guided install that is typical
the extended partition contains a single partition
use a live cd and post what is in your [FONT=Courier New]/boot/grub/grub.cfg[/FONT] or [FONT=Courier New]/boot/grub/menu.lst[/FONT]
a gparted screen shot of the drive would be nice also

---

### Post by ajgreeny on 2011-06-07
Has the computer crashed at any point before this problem.  I had similar error messages after a crash some time ago, so I can't remember the detail of the error message, but all was well after booting a live CD/USB and then running ```
sudo e2fsck /dev/sda1
``` where sda1 was my ubuntu root OS partition.

Try that; it can do no harm.

---

### Post by sanderd17 on 2011-06-07
> **pqwoerituytrueiwoq said:**
> 
use a live cd and post what is in your [FONT=Courier New]/boot/grub/grub.cfg[/FONT] or [FONT=Courier New]/boot/grub/menu.lst[/FONT]
a gparted screen shot of the drive would be nice also

An alternative for this (which gives us more information): run the boot info script and post the output:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Randy_Rhoads on 2011-06-08
Thank you very much for you replies.

> Quote:
                                                                      Originally Posted by **pqwoerituytrueiwoq**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10912387#post10912387")                 
                 [I]use a live cd and post what is in your [FONT=Courier New]/boot/grub/grub.cfg[/FONT] or [FONT=Courier New]/boot/grub/menu.lst[/FONT]
a gparted screen shot of the drive would be nice also[/I]
                                 
An alternative for this (which gives us more information): run the boot info script and post the output:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)1) Using a live-CD, in my /boot/grub/ there is only grubenv  which contians "Grub environment block"

2) "sudo boot_info_script.sh" freezes tring to analyze sda

3) I have tried to repair with gparted sda1, here is the result:

```
GParted 0.5.1
 Libparted 2.2
    Check and repair file system (ext4) on /dev/sda1  00:00:03    ( ERROR )             calibrate /dev/sda1  00:00:00    ( SUCCESS )             path: /dev/sda1
start: 2048
end: 970817535
size: 970815488 (462.92 GiB)          check file system on /dev/sda1 for errors and (if possible) fix them  00:00:03    ( ERROR )             e2fsck -f -y -v /dev/sda1             Filesystem mounted or opened exclusively by another program?
      e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Device or resource busy durante l'apertura di /dev/sda1 
            ========================================

```4) even if I try to mount sda1 with gigolo, I get this:

```
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending
```any suggestion?
Thank you, bye!

---

### Post by ajgreeny on 2011-06-09
> **Randy_Rhoads said:**
> Thank you very much for you replies.

1) Using a live-CD, in my /boot/grub/ there is only grubenv  which contians "Grub environment block"

2) "sudo boot_info_script.sh" freezes tring to analyze sda

3) I have tried to repair with gparted sda1, here is the result:

```
GParted 0.5.1
 Libparted 2.2
    Check and repair file system (ext4) on /dev/sda1  00:00:03    ( ERROR )             calibrate /dev/sda1  00:00:00    ( SUCCESS )             path: /dev/sda1
start: 2048
end: 970817535
size: 970815488 (462.92 GiB)          check file system on /dev/sda1 for errors and (if possible) fix them  00:00:03    ( ERROR )             e2fsck -f -y -v /dev/sda1             Filesystem mounted or opened exclusively by another program?
      e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Device or resource busy durante l'apertura di /dev/sda1 
            ========================================

```4) even if I try to mount sda1 with gigolo, I get this:

```
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending
```any suggestion?
Thank you, bye!
1.  That is in the /boot/grub of the live CD; you need to mount and look at the /boot/grub of your installed version in /media/diskname/boot/grub/

2.  The command is ```
sudo ./boot_info_script.sh
```You missed the ./ from the command.

3.  The partition you are using fsck on must be unmounted.

4.  No idea about gigolo, but it suggests that the partition is in use (mounted?).

---

### Post by Randy_Rhoads on 2011-06-13
Hello everybody, thank u for the suggestion, I am still missing the solution.
> 
1.  That is in the /boot/grub of the live CD; you need to mount and look  at the /boot/grub of your installed version in  /media/diskname/boot/grub/

2.  The command is      Code:
     sudo ./boot_info_script.sh 
You missed the ./ from the command.I have tried it, but it still freezes while "Retriving information from /dev/sda1..."


> 3.  The partition you are using fsck on must be unmounted.

4.  No idea about gigolo, but it suggests that the partition is in use (mounted?). 
If I have well understood, the solution is to properly mount sda1 in order to retrive information from grub and eventuallly repair the filesystem,  
Therefore I tried this:

```

ubuntu@ubuntu:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
ubuntu@ubuntu:~$ sudo mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
```here's /etc/fstab
```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```and /etc/mtab 
```
aufs / aufs rw 0 0
none /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
/dev/sr0 /cdrom iso9660 ro,noatime 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0

```Any Idea? Should I edit these tables?
tnk u, bye! :D

---

### Post by sanderd17 on 2011-06-13
> **Randy_Rhoads said:**
> Hello everybody, thank u for the suggestion, I am still missing the solution.
I have tried it, but it still freezes while "Retriving information from /dev/sda1..."

this is very weird, try it again, redownload the script and only execute that, without doing anything else (don't look at files on your hdd ...)

Give us the full terminal contents, including what you typed.
> 

If I have well understood, the solution is to properly mount sda1 in order to retrive information from grub and eventuallly repair the filesystem, 

NO, you cannot work with mounted disks, you should leave it unmounted. Mounting happens when you look at a file, so there is no real need for CLI.

---

### Post by Randy_Rhoads on 2011-06-13
> **sanderd17 said:**
> this is very weird, try it again, redownload the script and only execute that, without doing anything else (don't look at files on your hdd ...)

Give us the full terminal contents, including what you typed.


NO, you cannot work with mounted disks, you should leave it unmounted. Mounting happens when you look at a file, so there is no real need for CLI.
[FONT=Arial]
I just tried to mount sda1  to see[/FONT][FONT=Arial] /boot/grub/grub.cfg or [/FONT][FONT=Arial]/boot/grub/menu.lst.
Anyway sda1 is not mounted and[/FONT][FONT=Arial] can[/FONT][FONT=Arial]'t mount it*. *[/FONT][FONT=Courier New][FONT=Arial]Regarding boot_info_script, here's what I have done:
[/FONT][/FONT]```
[FONT=Courier New]
ubuntu@ubuntu:~/Desktop$ sudo bash ./boot_info_script.sh

boot_info_script version: 0.60        [17 May 2011]

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... [/FONT]
```[FONT=Courier New][FONT=Arial]

I tried 3 times (rebooting from the liveCD) and It freezes always at this point and I can't stop the process with ctrl+c. Sda1 is not mounted:

[/FONT][/FONT]```
[FONT=Courier New]
ubuntu@ubuntu:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
ubuntu@ubuntu:~$ 
[/FONT]
```[FONT=Courier New][FONT=Arial]

[/FONT][/FONT]

---

### Post by sanderd17 on 2011-06-13
if it is not mounted, you can not mount it and no program is able to investegate it, then there is certainly something very wrong with that partition.

If it is possible, I should format it. I can't be of further help I fear.

---

### Post by Randy_Rhoads on 2011-06-13
> **sanderd17 said:**
> if it is not mounted, you can not mount it and no program is able to investegate it, then there is certainly something very wrong with that partition.

If it is possible, I should format it. I can't be of further help I fear.

Don't worry and thank u for the support, It is a new 500GB HD with linux and very few data, I will try to fix the partition or recover the data with testdisk. If i can't format I will return the HD to the shop.... very strange.

Thank u anyway!;)

---

### Post by Randy_Rhoads on 2011-06-14
I could not repair the partition but I will show what I have done, maybe it will be useful to someone in future.

PROBLEMS:

I couldn't repair the partition with Gparted, nor mount it, but it resulted "in use". 
Another strange thing is that the process of installing ubuntu with liveCD stopped before partition resizing step. 
I succeeded in saving my data with testdisk. 
For a strange reason my Xubuntu 10.04 liveCD froze in installing testdisk with the command:

```
sudo apt-get install testdisk
```It downloaded the package but froze during unpacking... 

WHAT I HAVE DONE:

therefore I downloaded the static version from:

[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

I extracted the folder, opened a terminal in it and launched:
```

sudo ./testdisk_static
```Following the instructions, in the section advanced>list I could look at the content of the broken partition and save my files on an usb key/external HD (I recoverd ~/-config too in order to reestablish some of the xfce and other programs setup after Xubuntu installation).
Then I erased the partition table with gparted (WARNING: this operation "cause the lost" of all the data from your HD, anyway they were still visible with testdisk).
Finally I rebooted from the same liveCD and installed Xubuntu 10.04 on the entire HD. It is working well, no more boot problems. :KS

Bye!

---

### Post by BartlettMagic on 2012-09-25
i myself am also a newb and having the same problems.  a friend of mine who i was consulting suggested also that there might be serious issues with the disk.  thankfully i found this thread... i will be following the suggestions listed above, i just wanted to go on record as saying that this is not an isolated incident.  

up to this point, i have tried

$ sudo mkdir /mnt/drive

$ sudo mount /dev/sda1 /mnt/drive

and at this point it hangs.

---

