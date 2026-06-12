---
title: "Attempted ubuntu install damages something, need help to get back on feet...."
date: 2012-02-09
forum: General Help
---

### Post by BruceAlakae on 2012-02-09
I downloaded the latest ubuntu version, and used the provided instructions to make a live USB drive from it.  Runs and works fine from the USB drive, but I tried to install ubuntu on my HD with it, and at the point where it was creating a new partition (cut out of space from a win 7 partition) it worked for a while and then gave an error, I forget exactly what, just said operation failed, aborting basically.  

I have been trying to fix this for 3 days now in one way or another.  When I boot into ubuntu from the drive again Gparted the partition editor tool says there is an error with one of the partitions ("parttwoprimary") (which is not the same partition I told the ubuntu installer to carve the new partition out of) and to run chkdsk /f in windows.  I cannot access the data off of it and need to copy it off.


The whole reason I was trying to install ubuntu was so I could get the data off of the computer, which for various reasons I could not find a way to do using the live usb.  I can't boot into windows.   I have tried various methods including trying to make a live USB with some version of windows on it using bartPE etc. but the software has too many defects and cannot be made to work with my system. 

 I have to sell the computer tomorrow at 5 pm and have to go for a blood test tomorrow at 7 am.  Any ideas?  I am hoping someone can point me to some sort of live usb image that can be used to fix this problem when I get back from the hospital tomorrow.... or maybe some sort of utility that can fix the partition table under ubuntu or whatever.  I just need to get my data off (3 gb or so...)

---

### Post by sikander3786 on 2012-02-09
Welcome to the forums. :)

Sorry to hear about your problems. As you said you are able to boot Ubuntu Live USB successfully on that PC, you shouldn't need to install Ubuntu in order to get your data off that PC. I guess your data is contained on a separate partition and not the Windows one? Regardless of where it is, you should be able to extract it equally well from both Windows and non-Windows partitions.

I don't know which desktop environment is loading by default for you. As you said you've downloaded the latest version, it must be either Unity (3D) or Unity 2D. From either of those, press Alt + F2 and type:

```
nautilus
```

A file browser should open up. You can also open it by clicking the 'home' (folder) icon in the launcher on the left edge of your screen. In the left column in file browser, it should be showing your existing partition. Clicking any of those would mount and open it automatically and then you should be able to copy & paste your data to another place. If you wish to copy it to another USB drive, simply plug it and it should also appear in the same left column in the file browser.

If it doesn't work for you, press Alt + F2 and type:

```
gnome-terminal
```

In the Terminal window that opens up (DOS-like), type this command:

```
sudo fdisk -lu
```

And copy & paste the output over here so that we can take a look.

---

### Post by Mark Phelps on 2012-02-09
Don't know how far away "tomorrow" was when you first wrote this ... but it's been 5 hours already, you have YET to respond -- and you're running out of time!

We can't help you if you don't help us ...

---

### Post by BruceAlakae on 2012-02-09
Hello Mark, yes you are quite right, thanks for the help...sorry but this is my first opportunity to start on this as I had those appointments at the hospital and stuff.  I'll do the fdisk thing now.  Thanks for the help.

---

### Post by BruceAlakae on 2012-02-09
Okay I used a cd with some other linux distro because I realized I had overwritten my ubuntu usb drive with stuff as I attempted to boot into windows  and it takes forever to re-write it with ubuntu...



sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    94651199    47325568+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2        94651200   103859279     4604040    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3   *   103859280   122762391     9451556    7  HPFS/NTFS
/dev/sda4       148795390   156301311     3752961    5  Extended
/dev/sda5       148795392   154224639     2714624   83  Linux
/dev/sda6       154226688   156301311     1037312   82  Linux swap

---

### Post by BruceAlakae on 2012-02-09
It is the sda3 partition I need the data off of.  When I view the partition konqueror it says there are no files... there are 3 gb of data on there I need.

---

### Post by brpylko on 2012-02-09
In the installer did you make sure to set the boot partition to be on the same device as the install location? If you didn't, that could cause problems.

---

### Post by BruceAlakae on 2012-02-09
I don't recall such an option being involved... but I don't think that is the problem as that would not have resulted in errors during the partitions modification process right?  Something happened while it was changing the partitioning I think, and it damaged the partition table I guess.

---

### Post by BruceAlakae on 2012-02-09
So, ah, any ideas anyone? Have to sell this thing at 5 pm remember.

---

### Post by cryptotheslow on 2012-02-09
> **BruceAlakae said:**
> It is the sda3 partition I need the data off of.  When I view the partition konqueror it says there are no files... there are 3 gb of data on there I need.

How are you "viewing" the partition?

It will need to be mounted to somewhere in order to view the contents.

Can you post up the output of the command:
```
mount
```So we can see what is mounted where.


Oh - and as people here are all over the world - we have no idea how long away 5pm is for you!

---

### Post by Mark Phelps on 2012-02-09
> **cryptotheslow said:**
> Oh - and as people here are all over the world - we have no idea how long away 5pm is for you!

Yeah -- I'd like to know this, too!

If Win7 is still working, a brute-force, quick-and-dirty solution, presuming you have an external drive or a USB drive big enough to hold the data partition ... is to do the following:
1) Download and install the FREE version of Macrium Reflect (MR) in Win7
2) Connect the external drive or USB stick and use MR to image the data partition to that destination.

NOW, if this works, you have an image copy of that drive -- which you can restore to another Windows PC and use that to recover your data.

However, if you're also concerned about wiping the Ubuntu data off your hard drive, you would need to do the following (as one approach):
1) Boot using an Ubuntu desktop CD
2) Select the option to Try Ubuntu
3) Install dban
4) Run dban -- to wipe the Ubuntu partition from your hard drive

---

### Post by BruceAlakae on 2012-02-09
mount
aufs on / type aufs (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/sda2 on /mnt/sda2 type vfat (rw,noatime,quiet,umask=0,check=s,shortname=mixed)
/dev/sdb1 on /mnt/sdb1 type vfat (rw)
/dev/sda1 on /mnt/sda1 type ntfs (rw)


To view it I just opened Konqueror and click on "storage devices" and navigate from there.  When I was using the latest ubuntu livecd I just clicked on the "home" icon on the taskbar amd it opened a similar file browser, probably the nautilus thing I guess.  But it worked before under linux, that is before I tried to instal linux to the hd as described above.

---

### Post by BruceAlakae on 2012-02-09
oh sorry it's est.  5pm is in 4 hours, and I better leave in 3 hours and 30 :(!

---

### Post by cryptotheslow on 2012-02-09
OK so sda3 is not currently mounted.

These two commands should mount it:
```
sudo mkdir -p /mnt/sda3
sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda3 /mnt/sda3
```

If the distribution you are now using does not use sudo then you can just leave sudo off the front of the commands - presuming you are currently logged in as root (or equivalent).

If that mounts you can use Konqueror and browse the filesystem to find /mnt/sda3 which should hold the files you need.

If you get any errors mounting post them back here.

---

### Post by BruceAlakae on 2012-02-09
sudo mkdir -p /mnt/sda3
sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda3 /mnt/sda3
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

:(
I think konqueror refused to mount it for similar reasons. It (for the first time) just gave me an error message which I wasn't fast enough to catch and I can't reproduce now, but a bunch of stuff and telling me to again run chkdsk /f

---

### Post by BruceAlakae on 2012-02-09
just tried "dmesg" at the prompt:

ailed for RX frame from b0:e7:54:a7:5b:59 (res=-3)=-2)

wmaster0: TKIP decrypt failed for RX frame from b0:e7:54:a7:5b:59 (res=-2)
NTFS-fs error (device sda3): ntfs_read_inode_mount(): Failed to load the complet
e runlist for $MFT/$DATA. Driver bug or corrupt $MFT. Run chkdsk.
NTFS-fs error (device sda3): ntfs_read_inode_mount(): Failed. Marking inode as b
ad.
NTFS-fs error (device sda3): ntfs_fill_super(): Failed to load essential metadat
a.
wmaster0: TKIP decrypt failed for RX frame from b0:e7:54:a7:5b:59 (res=-3)
wmaster0: TKIP decrypt failed for RX frame from b0:e7:54:a7:5b:59 (res=-3)
wmaster0: TKIP decrypt failed for RX frame from b0:e7:54:a7:5b:59 (res=-3)
wmaster0: TKIP decrypt failed for RX frame from b0:e7:54:a7:5b:59 (res=-2)
wmaster0: TKIP decrypt failed for RX frame from b0:e7:54:a7:5b:59 (res=-2)
NTFS-fs error (device sda3): ntfs_read_inode_mount(): Failed to load the complet
e runlist for $MFT/$DATA. Driver bug or corrupt $MFT. Run chkdsk.
NTFS-fs error (device sda3): ntfs_read_inode_mount(): Failed. Marking inode as b
ad.
NTFS-fs error (device sda3): ntfs_fill_super(): Failed to load essential metadat
a.
NTFS-fs error (device sda3): ntfs_read_inode_mount(): Failed to load the complet
e runlist for $MFT/$DATA. Driver bug or corrupt $MFT. Run chkdsk.
NTFS-fs error (device sda3): ntfs_read_inode_mount(): Failed. Marking inode as b
ad.
NTFS-fs error (device sda3): ntfs_fill_super(): Failed to load essential metadat
a.
NTFS-fs error (device sda3): ntfs_read_inode_mount(): Failed to load the complet
e runlist for $MFT/$DATA. Driver bug or corrupt $MFT. Run chkdsk.
NTFS-fs error (device sda3): ntfs_read_inode_mount(): Failed. Marking inode as b
ad.
NTFS-fs error (device sda3): ntfs_fill_super(): Failed to load essential metadat
a.
NTFS-fs error (device sda3): ntfs_read_inode_mount(): Failed to load the complet
e runlist for $MFT/$DATA. Driver bug or corrupt $MFT. Run chkdsk.
NTFS-fs error (device sda3): ntfs_read_inode_mount(): Failed. Marking inode as b
ad.
wmaster0: TKIP decrypt failed for RX frame from b0:e7:54:a7:5b:59 (res=-2)
wmaster0: TKIP decrypt failed for RX frame from b0:e7:54:a7:5b:59 (res=-2)
printk: 1 messages suppressed.
NTFS-fs error (device sda3): ntfs_read_inode_mount(): Failed to load the complet
e runlist for $MFT/$DATA. Driver bug or corrupt $MFT. Run chkdsk.
wmaster0: TKIP decrypt failed for RX frame from b0:e7:54:a7:5b:59 (res=-2)
wmaster0: TKIP decrypt failed for RX frame from b0:e7:54:a7:5b:59

snip

(res=-2)
wmaster0: TKIP decrypt failed for RX frame from b0:e7:54:a7:5b:59 (res=-2)
wmaster0: TKIP decrypt failed for RX frame from b0:e7:54:a7:5b:59 (res=-2)
wmaster0: TKIP decrypt failed for RX frame from b0:e7:54:a7:5b:59 (res=-2)
wmaster0: TKIP decrypt failed for RX frame from b0:e7:54:a7:5b:59 (res=-2)
printk: 2 messages suppressed.
NTFS-fs error (device sda3): ntfs_read_inode_mount(): Failed to load the complet
e runlist for $MFT/$DATA. Driver bug or corrupt $MFT. Run chkdsk.
NTFS-fs error (device sda3): ntfs_read_inode_mount(): Failed. Marking inode as b
ad.
NTFS-fs error (device sda3): ntfs_fill_super(): Failed to load essential metadat
a.
wmaster0: TKIP decrypt failed for RX frame from b0:e7:54:a7:5b:59 (res=-3)
wmaster0: TKIP decrypt failed for RX frame from b0:e7:54:a7:(res=-2)
wmaster0: TKIP decrypt failed for RX frame from b0:e7:54:a7:5b:59 (res=-2)
wmaster0: TKIP decrypt failed for RX frame from b0:e7:54:a7:5b:59 (res=-3)
wmaster0: TKIP decrypt failed for RX frame from b0:e7:54:a7:5b:59 (res=-2)
wmaster0: TKIP decrypt failed for RX frame from b0:e7:54:a7:5b:59 (res=-2)


there were more of those tkip /whatever messages which I snipped out for clarity, presumably stuff with the wireless connection of course so not relevant.

---

### Post by cryptotheslow on 2012-02-09
```
NTFS-fs error (device sda3): ntfs_read_inode_mount(): Failed to load the complet
e runlist for $MFT/$DATA. Driver bug or corrupt $MFT. Run chkdsk.
```

Looks like the file-table is corrupt on the partition.

Does your Windows installation still boot? If so you need to run chkdsk on the partition.

---

### Post by BruceAlakae on 2012-02-09
> **cryptotheslow said:**
> ```
NTFS-fs error (device sda3): ntfs_read_inode_mount(): Failed to load the complet
e runlist for $MFT/$DATA. Driver bug or corrupt $MFT. Run chkdsk.
```Looks like the file-table is corrupt on the partition.

Does your Windows installation still boot? If so you need to run chkdsk on the partition.

No :(. I have been trying to run chkdsk somehow but it is very hard/unreliable to get a solution for booting from usb to windows or even cd afaik.  yes there is bartpe etc. but they don't work for me and it is because of defects in the software.

---

### Post by cryptotheslow on 2012-02-09
You may have some luck using Boot Repair to fix up your booting problems.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Alternatively a Windows Repair disk would be able to repair the boot record - leaving you with a system with just the option to boot into Windows.

If you don't have a Repair / Rescue disk this may be of some use to get hold of an XP Recovery Console image you can burn:
[http://www.geekstogo.com/forum/topic/231709-how-to-run-chkdsk-on-ntfs-drive-when-i-cannot-boot-windows/](http://www.geekstogo.com/forum/topic/231709-how-to-run-chkdsk-on-ntfs-drive-when-i-cannot-boot-windows/)

Is sda3 actually your Windows installation or is it a separate data partition?

---

### Post by BruceAlakae on 2012-02-09
> **cryptotheslow said:**
> You may have some luck using Boot Repair to fix up your booting problems.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Alternatively a Windows Repair disk would be able to repair the boot record - leaving you with a system with just the option to boot into Windows.

Is sda3 actually your Windows installation or is it a separate data partition?

I have 2 separate xp installations, one on preload and one on the parttwo one so yeah I will try this.

---

### Post by BruceAlakae on 2012-02-10
I had to cancel my meeting to sell.  I have until wed now to get this fixed.

---

### Post by cryptotheslow on 2012-02-10
That's handy - how's things coming along?

---

### Post by BruceAlakae on 2012-02-14
Thanks for asking, but terrible.  I bought some CDs, and went through trying to run chkdsk with the Ultimate Boot CD thing, and also with a win xp cd.  The UBCD sucks too much (lacks the feature) and the Win xp CD recovery console fails to acknowledge my computer even has a hard drive telling me to make sure it is even plugged in!  

My current goal is to run chkdsk!  That's it!

---

### Post by BruceAlakae on 2012-02-14
****! I ran chkdsk like it said to and it didn't work?  Where the **** is my data??  This whole thing has been off the wall.  I did everything I was supposed to do and the software spontaneously ****** everything up.  This isn't 1998, why the @%!# hasn't this **** been worked out yet?

Any ideas???

---

### Post by cryptotheslow on 2012-02-14
What doesn't appear clear is what the original problem was - was Win7 already unbootable hence the need to use a linux distro to recover files?

Two possible avenues come to mind now:

a. Plug the drive into another PC with a working Win OS and force chkdsk on it again from there.

b. Look into using Testdisk and Photorec.

Testdisk can find and restore previous partition schemas.

Photorec will do a partition agnostic scan of the entire disk for recoverable files ignoring any issues with partition layouts or file table corruption - make sure to set the location to recover to, to an external medium e.g. usb drive or key

Photorec comes as part of the Testdisk package and is available in the repositories.


Some initial reading:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

### Post by BruceAlakae on 2012-02-15
Yes I did try testdisk as I thought that might be it, and it told me there were file system errors.  A couple hours ago I got chkdsk /f to run from the xp command console.  That seems to have repaired most of it although there is a "found.000" folder with about 34 megs of stuff in it it looks like I got all the important stuff back.

Thanks for the help.  I very much admire the FOSS community and have donated $$ in the past but when you go to install the software in a straightforward way and it spontaneously destroys stuff without so much as a warning as to the possibility of that happening then that's pretty ridiculous.  I guess I have to donate even more money so the next version is better :P.  Oh well.

---

### Post by BruceAlakae on 2012-02-15
And to be fair, the original problem was an attempt to install win 7 in the first place.  I tried to install win 7 and it failed to boot from that point on.  There was a win 7 partition but it had never run win 7.  I probably could have repaired in some way but decided to just get the data off, and do a wipe and install instead.  Had some problems using ubuntu that I thought might be resolved by installing it to the hd and there I was, 2 steps back...

And they guy emailed me back just about at 12 to say he decided not to buy it.  Whatever I'll probably find another buyer but it is a hassle.

---

