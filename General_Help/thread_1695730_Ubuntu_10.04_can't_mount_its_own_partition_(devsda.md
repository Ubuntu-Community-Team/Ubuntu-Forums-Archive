---
title: "Ubuntu 10.04 can't mount its own partition (/dev/sda1)"
date: 2011-02-26
forum: General Help
---

### Post by HorseBox on 2011-02-26
I'm not a complete noob but I'm completely lost here and don't know what to do. I turned on my laptop today and noticed a load of unfamiliar startup text so I knew something was wrong. Now whenever I startup my laptop, GRUB loads fine but when I try to start Ubuntu it says the following:

> 
mount : mounting /dev on /root/dev failed : No such file or directory
mount : mounting /sys on /root/sys failed : No such file or directory 
mount : mounting /proc on /root/proc failed : No such file or directory
Target filesystem doesn't have /sbin/init
No init found. try passing init= bootarg
Busybox 1.13.3 ( Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)

(initramfs)
so all I'm left with is this BusyBox command prompt. I'm on a live Ubuntu CD right now and if I try to mount /dev/sda1 either in the terminal (with the mount command) or with the GUI it just gets stuck. 

I found a few threads about this same problem but the only really useful one
[http://www.backports.ubuntuforums.org/showthread.php?t=1244466](http://www.backports.ubuntuforums.org/showthread.php?t=1244466)
is closed so I can't reply to it. On that thread someone gave a useful reply and said
> Not sure what has happened here, but could you please boot a live cd and mount your system with the following

This will provide you with a list of your drives and partitions, you  need to pick the one that your root file system is installed to, it will  be something like /dev/sda1but in my case I can't even mount /dev/sda1. When I run sudo fdisk -l heres what I get
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12158    97656832   83  Linux
/dev/sda2           12159       12644     3903764+   5  Extended
/dev/sda3   *       12645       12657      102400    7  HPFS/NTFS
/dev/sda4           12657       19458    54623232    7  HPFS/NTFS
/dev/sda5           12159       12644     3903763+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
The NTFS partition(s) have Windows 7 installed on it and it works fine but /dev/sda1 is my Ubuntu partition and thats the one that won't mount. I followed the instructions on that other thread and entered the command
```
sudo e2fsck -fyv /dev/sda1
```and heres what happened
> ubuntu@ubuntu:~$ sudo e2fsck -fyv /dev/sda1
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ 
thats weird because I rebooted with a live Ubuntu CD and didn't even try to mount /dev/sda1 this time. The instructions were to then try to mount the drive from the GUI so heres what happens when I do that: it attempted to mount it for about a minute then gave me this error message
[IMG]http://img716.imageshack.us/img716/857/screenshot1xky.png[/IMG]
When I tried again heres the error it gave me
[IMG]http://img87.imageshack.us/img87/1478/screenshot2gc.png[/IMG]
The problem seems to be that /dev/sda1 can't be mounted for some reason. I don't know what that error message means and I don't know what else I can do to further diagnose /dev/sda1 and find out why it can't be mounted. Ordinarily I'd just reinstall Ubuntu but I have a couple of lab reports that I had saved on that partition so I'm in trouble if I can't figure out how to access the partition. Any help at all would be greatly appreciated.

EDIT: At the end of that other thread someone recommends to use testdisk to recover the data from the partition. All I really need to do is get those lab reports back but I had them saved inside a Windows 7 guest on Virtual Box. Will this complicate matters a lot for me?

UPDATE: I tried to reinstall Ubuntu and it wouldn't work. Seems this is a bigger problem than I suspected. Does this mean my harddrive is corrupted? I can still use the Windows 7 partition but I take it that the Ubuntu installer not working is a bad sign.

---

### Post by oldfred on 2011-02-26
One or two others could not mount partitions with Ubuntu to run e2fsck. 

Several were able to run the file checks with slatz. Download a slatz or other different distribution liveCD and boot with that to run the e2fsck.

From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1


There is something not umounting correctly, but I do not know what that may be.

---

### Post by HorseBox on 2011-02-26
> **oldfred said:**
> One or two others could not mount partitions with Ubuntu to run e2fsck. 
I burned a live slax CD and used it to run e2fsck and IT WORKED!!! It repaired the partition in a matter of seconds. I'd just about given up on this and was ready to buy a new harddrive so you saved me a whole load of trouble. :grin: Thanks a lot!

---

### Post by oldfred on 2011-02-26
Glad it worked, one more on the list of those who found a work around. Not sure what is causing it not to mount in the first place. 

Normally I use Ubuntu for everything, but now I keep a couple of other ISO's on my flash drive 'just in case'.

---

