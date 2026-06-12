---
title: "Daft Question perhaps, trying to find....."
date: 2009-07-03
forum: General Help
---

### Post by DocLogic on 2009-07-03
Greets All,

   Using JJ (9.04) and have a 'need' I have not been able to satisfy..
Is there a package, that would be usable both on a desktop, and particularity on a live CD, or other boot-able media scenario that can not only look at a hard disc in question, but identify not only partitions but file systems, and allow you to browse said file systems. This would be similar to forensics utilities but with out that much depth. Can be a simple console utility since I would be starting from power down anyway, thus less wait for X to load...
   I keep a very extensive "junk box" that is always changing. I acquire lots of dead, outdated, or other wise retired machines and/or parts. So I test parts and stock what is good. This of course includes my lazy habit of sitting a hard disc aside and using another for some test or project, then forgetting if there is anything on it that needed to be kept LOL. Then find my self doing an install of some type, not always Linux, and pick up a drive and end up jumping through many hoops to determine if I need anything off of that drive before wiping it out.....

---

### Post by blueridgedog on 2009-07-03
This disk should get you started:

[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

Note that you have all the tools you need with fdisk and mount.

If you want to see what disks are in the system:

sudo fdisk -l

That will even give you partitions and formats.

Mount (mount) will give you access to them all.

---

### Post by DocLogic on 2009-07-04
Thanks! Although, fdisk is currently how I do find out what partitions are there, I was actually looking for a little more reporting.
Example:

fdisk would return something like;

/dev/sda3  262  3739  27937035  83  Linux

Is there something that also mines the partition for file system info such as;

/dev/sda3  262  3739  27937035  83  Linux reiserfs use=72%

This is hypothetical, but the idea is reporting on not just the partition type, but the actual file system format as well, (not limited to Linux). I have heard of disk 'explorers' that do not even require mounting the partition in question, I just don't know what or where to find.

Doc.

---

### Post by earthpigg on 2009-07-04
a regular ubuntu live cd includes gparted and nautilus.

gparted is an outstanding graphical tool that allows you to view/move/erase/etc partitions, and nautilus is the default ubuntu file manager.

---

### Post by niteshifter on 2009-07-04
Hi,

[QUOTE=blueridgedog]sudo fdisk -l

That will even give you partitions and formats.[/QUOTE]

[QUOTE=DocLogic]Is there something that also mines the partition for file system info such as;

/dev/sda3  262  3739  27937035  83  Linux reiserfs use=72%[/QUOTE]

What fdisk reports for file system type is a "hint" - it's what the partition was marked as by the partition table editor before the file system is created via mkfs. So it (the partition table marking) is not always going to match the file system type that's on it, there's no guarantee here.

The file command can be used like this:
```
file -sL /dev/sdXY
```
to retrieve info about special files / block devices like partitions.

---

### Post by cariboo on 2009-07-04
Almost all the tools you need are on the Live CD. Fdisk, hdparm, blkid and gparted. The only thing that isn't on the Live CD is smartmontools. If you play system is always changing why not set the system up with all the tools you need, then use something like [remastersys]("http:///www.geekconnection.org/remastersys/remastersystool.html") to create custom setup.

---

### Post by blueridgedog on 2009-07-04
> **niteshifter said:**
> 
What fdisk reports for file system type is a "hint" - it's what the partition was marked as by the partition table editor before the file system is created via mkfs.

Excellent information...I did not know that.

The suggestion to use remastersys is great...you could even put it on a USB key!

---

### Post by DocLogic on 2009-07-04
> **niteshifter said:**
> Hi,





What fdisk reports for file system type is a "hint" - it's what the partition was marked as by the partition table editor before the file system is created via mkfs. So it (the partition table marking) is not always going to match the file system type that's on it, there's no guarantee here.

The file command can be used like this:
```
file -sL /dev/sdXY
```
to retrieve info about special files / block devices like partitions.

Very Correct night shifter, and Thanks.
  I am very familiar with fdisk, but not so much some of the newer tools out there. I have been using linux since Linux wasn't cool LOL.. like maybe 1990 or so starting with Slack 1.5 if memory serves. But again I was a user, more than a guru or hardcore hacker/coder. (Using the term hacker in it's proper perspective, not the 'media' perspective).
  Also if memory serves, the file command also relies on the given file system being mounted. What I am hoping for is to be able to examine an unmounted file system and determine what the format type is. fdisk is a great helper, particularly with non Linux native file systems, as FAT, JFS, VFAT, NTFS, etc are identified, but as for a *nix file system, one then has to guess whether or not we are dealing with ext2, ext3, reiserfs, etc. Including for the purpose of mounting the partition if one is running a totally minimal system for the test bed.

  I am looking at the Ubuntu-rescue-remix LiveCD and from what I am seeing it is quite nicely equipped. though all in all I am aiming to script the ID process to automate as much as possible. Right now when I plug in an unknown drive or drives, I am using fdisk with grep such as...

fdisk -l | grep -f patternfile >> temp_test.dat

where patternfile is a regular file listing possible device matches ie:

dev/sda1
dev/sda2
.
.
dev/hdd4

the result in temp_test.dat is a parsed list of partitions with no other information to be parsed and scripted to what ever I end up using to investigate the drive. But of course if I am dealing with a Linux partition as of right now, assuming modular (non-auto for light weight), I have to attempt to mount as ext2, failing that, attempt as ext3, failing that attempt as reiserfs, etc until it is successfully mounted.
The preference would of course be to first examine the partition with out mounting.

Now have a gone totally bazoonkers? LOL

Doc.

---

### Post by DocLogic on 2009-07-04
> **cariboo907 said:**
> Almost all the tools you need are on the Live CD. Fdisk, hdparm, blkid and gparted. The only thing that isn't on the Live CD is smartmontools. If you play system is always changing why not set the system up with all the tools you need, then use something like [remastersys]("http:///www.geekconnection.org/remastersys/remastersystool.html") to create custom setup.

Tools are the key, That is what I am trying to figure out, is what exact tools I need to be using to make life easier :). I looked at the remastersystool it looks to be a very nice utility but I don't see where it would help me unless I want to actually backup one of the test target drives. as far as the play system, it is standalone, but I want to make it simpler yet, possibly even on a 486, or P1 with minimal memory and very much dedicated to this task. If I perfect it the way I think I can do, then I will attempt to recreated it as an embedded system, as a universal bench top test tool.

---

