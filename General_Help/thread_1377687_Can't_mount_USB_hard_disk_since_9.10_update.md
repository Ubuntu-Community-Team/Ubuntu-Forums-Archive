---
title: "Can't mount USB hard disk since 9.10 update"
date: 2010-01-10
forum: General Help
---

### Post by styleruk on 2010-01-10
Hi All

Bit of a silly one really.  I've had this external drive for ages, it contains all my music and pictures that I generally share on my network to my family etc...
It has been working for years on Ubuntu until the other month I updated to 9.10 and now it will not mount.
It still works on my EEE PC, I plug the USB in and up it pops as usual, however, I can't get it to work on Ubuntu 9.10

This is my 'fstab' file...[I]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=107fa297-8d4b-4586-a6c5-accc5c3098db /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=cb3afee2-54b3-43b7-8ec7-06ef096699cb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=130,devmode=664 0 0
/dev/sdi1 /media/SHARED vfat uid=1000,umask=022 0 0
/dev/sda1 /media/vmware ext2 defaults 0 0
/dev/sdc1 /media/raptor_3 ext3 defaults 0 0
/dev/sdd1 /media/raptor_2 ext3 defaults 0 0[/I]



It is listed as /dev/sdi1  and normally mounts as /media SHARED
If I run GParted, it shows up as /dev/sdi1 with an explanation mark. I'm reluctant to right-click fix it as it works, why should I fix it when it has nothing wrong with it.  And also, I run the risk of losing everything on it.  I do back it up but only when it's connected to Ubuntu...so catch 22 there.

Can anyone tell me what Ubuntu is doing wrong?

Si

---

### Post by LinuxRules1 on 2010-01-10
have you tried manually mounting it through terminal?

---

### Post by KrazyPenguin on 2010-01-10
How about a reboot with the USB hard disk plugged in???

---

### Post by styleruk on 2010-01-10
I've tried mount and it comes back with 'special device does not exist'.
I've tried rebooting with it plugged in and that don't work.

I've also just tried hashing out the fstab entry and rebooting with no change either.

---

### Post by SecretCode on 2010-01-10
Have you tried plugging it in and giving it plenty of time - at least 10 minutes - to mount? I've seen this happen when the system has activity on other usb ports.

With it plugged in, what's the output of
```
ls -l /dev/disk/by-path
```
```
sudo fdisk -l
```

---

### Post by sgosnell on 2010-01-10
This is a common Karmic problem.  It doesn't automount USB drives in many cases.  You can mount them through Nautilus or a terminal.  Nautilus is the easiest way for many, because you're going to browse the drive with it anyway most of the time.  Just click on the drive icon, and the drive will be mounted.  You have to tell Karmic to display the drive on the desktop or it won't be shown.

---

### Post by styleruk on 2010-01-11
Firstly, sgosnell.  I have tried this and nothing, the fact that gparted has found it and thinks it's bad tells me it's something else.  I know what you mean though, when it was working I sometimes have to mount it or wait a while.

Secondly SecretCode

running ls -l /dev/disk/ski sends back 'no such file or directory', obvious because it is not mounted.

Running sudo fdisk -l  gives below.  Not much really.


[I]Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b637abf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9964    80035798+  83  Linux

Disk /dev/sdb: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27192718

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        8666    69609613+  83  Linux
/dev/sdb2            8667        9039     2996122+   5  Extended
/dev/sdb5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdc: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc1b403d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9039    72605736   83  Linux

Disk /dev/sdd: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x75b2d746

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        9039    72605736   83  Linux

Disk /dev/sdi: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a4bad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1        9964    80035798+   b  W95 FAT32
[/I]

---

### Post by SecretCode on 2010-01-11
Actually - for once - I meant this command to be typed in exaclty as in, without substituting your path! :) [FONT="Courier New"]by-path[/FONT] is a special directory that will tell you all the attached disks by device path.
```
ls -l /dev/disk/by-path
```


What messages do you get if you mount it manually?
```
sudo mkdir /media/sdi
```
if you don't already have a mount point for it

Then
```
sudo mount -t auto /dev/sdi /media/sdi
```
or
```
sudo mount -t vfat /dev/sdi /media/sdi
```

---

### Post by slakkie on 2010-01-11
Perhaps install the usbmount package.

---

### Post by styleruk on 2010-01-11
This is the reply I get with ls -l /dev/disk/by-path



lrwxrwxrwx 1 root root  9 2010-01-11 10:23 pci-0000:00:1d.7-usb-0:3:1.0-scsi-0:0:0:0 -> ../../sde
lrwxrwxrwx 1 root root  9 2010-01-11 10:22 pci-0000:00:1f.1-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root  9 2010-01-11 10:22 pci-0000:00:1f.1-scsi-0:0:1:0 -> ../../sr0
lrwxrwxrwx 1 root root  9 2010-01-11 10:22 pci-0000:00:1f.2-scsi-0:0:0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 2010-01-11 10:22 pci-0000:00:1f.2-scsi-0:0:0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2010-01-11 10:22 pci-0000:00:1f.2-scsi-0:0:0:0-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2010-01-11 10:22 pci-0000:00:1f.2-scsi-0:0:0:0-part5 -> ../../sdb5
lrwxrwxrwx 1 root root  9 2010-01-11 10:22 pci-0000:00:1f.2-scsi-0:0:1:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 2010-01-11 10:22 pci-0000:00:1f.2-scsi-0:0:1:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 2010-01-11 10:22 pci-0000:00:1f.2-scsi-1:0:1:0 -> ../../sdd
lrwxrwxrwx 1 root root 10 2010-01-11 10:22 pci-0000:00:1f.2-scsi-1:0:1:0-part1 -> ../../sdd1

---

### Post by styleruk on 2010-01-11
Hang on hang on.  Something else just happened after a reboot!
An internal drive called /dev/sda1 is not mounting, GParted shows the same error!

---

### Post by SecretCode on 2010-01-11
Need this
> **SecretCode said:**
> What messages do you get if you mount it manually?
```
sudo mkdir /media/sdi
```
if you don't already have a mount point for it

Then
```
sudo mount -t auto /dev/sdi /media/sdi
```
or
```
sudo mount -t vfat /dev/sdi /media/sdi
```

---

### Post by styleruk on 2010-01-11
OK, now it's called sde and not sdi.  The internal drive is back again, I did a reboot and all is fine with that.

done the commands you asked and this is what I got...

simon@simon-desktop:~$ sudo mount -t auto /dev/sde /media/SHARED
mount: unknown filesystem type 'promise_fasttrack_raid_member'
simon@simon-desktop:~$ sudo mount -t vfat /dev/sde /media/SHARED
mount: wrong fs type, bad option, bad superblock on /dev/sde,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

simon@simon-desktop:~$

---

### Post by SecretCode on 2010-01-11
> **styleruk said:**
> ...
simon@simon-desktop:~$ sudo mount -t auto /dev/sde /media/SHARED
mount: unknown filesystem type 'promise_fasttrack_raid_member'
...

This tells me it's marked as part of a RAID system. And I have no experience of RAID.

---

### Post by styleruk on 2010-01-11
Neither do I, I have no idea how this happened!  I'm still reluctant to let GParted deal with it in case it scrubs it!

---

### Post by SecretCode on 2010-01-12
You might want to start a new thread 'USB hard disk appears as RAID' or something, and see if other people can have a look at the problem...

---

### Post by styleruk on 2010-01-12
> **slakkie said:**
> Perhaps install the usbmount package.

I've just tried that and no difference.

---

### Post by styleruk on 2010-01-12
Think I'm going to try to take everything off of it and let GParted do it's thing.  Out with the old iPod 80gb then!

---

### Post by slakkie on 2010-01-12
> **styleruk said:**
> I've just tried that and no difference.

Did you also edit /etc/usbmount/usbmount.conf ??

---

### Post by unc0nn3ct3d on 2010-02-19
Ah this is one of those threads that got me so excited because it looked to be about to solve my problem and then it just ended as the thread starter dropped away.. 

So I shall hijack it :)


So I'm experiencing the exact same problem except there is no RAID errors at all.  What happens is my USB port is a little loose so if the cable gets bumped the HDD will disconnect until I wiggle it and get it to reconnect.  about 50% of the time the HDD will reconnect fine and come back online but the rest of the time Ubuntu just plays dump and can't see it.  Everything I'm experiencing is basically exactly as has been discussed in this thread.

my fdisk -l produces this:

Disk /dev/sdd: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0037c986

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       85814   689300923+   7  HPFS/NTFS


My attempts to mount it with all sorts of switches all produce the same result:

mount: special device /dev/sdd1 does not exist


ls -l /dev/disk/by-path produces this:

total 0
lrwxrwxrwx 1 root root  9 2010-02-18 18:53 pci-0000:00:12.0-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root 10 2010-02-18 18:53 pci-0000:00:12.0-scsi-0:0:0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-02-18 18:53 pci-0000:00:12.0-scsi-0:0:0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-02-18 18:53 pci-0000:00:12.0-scsi-0:0:0:0-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 2010-02-19 01:14 pci-0000:00:13.5-usb-0:1:1.0-scsi-0:0:0:0 -> ../../sdd
lrwxrwxrwx 1 root root  9 2010-02-18 18:53 pci-0000:00:13.5-usb-0:4:1.0-scsi-0:0:0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 2010-02-18 18:53 pci-0000:00:13.5-usb-0:4:1.0-scsi-0:0:0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 2010-02-18 18:53 pci-0000:00:14.1-scsi-0:0:0:0 -> ../../sr0

I just installed USBmount and changed the usbmount.conf to include ntfs file systems but that did no good.  I can simply reboot the machine and it will come up fine but my curiosity is peaked and I want to figure out why this is happening and how I can fix it without the reboot.

Looking forward to continuing down this rabbit hole :)

---

### Post by unc0nn3ct3d on 2010-02-19
One more thing I noticed.

I found this in my /dev/.udev/failed directory:

lrwxrwxrwx 1 root root 88 2010-02-19 01:40 block:sdd -> /devices/pci0000:00/0000:00:13.5/usb1/1-2/1-2:1.0/host16/target16:0:0/16:0:0:0/block/sdd
 

Thought that was interesting

---

### Post by unc0nn3ct3d on 2010-02-19
Alright, I have progress!!!

I accidentally ran 'sudo MAKEDEV sdd' from inside /dev/.udev/failed (as it wouldn't work from inside of /dev/ ) and then noticed sdd1 - 11 in my /dev/.udev/failed and when I tried to mount sdd1 VIOLA! it works.. 

Still pretty backwards, there has to be a better solution

---

