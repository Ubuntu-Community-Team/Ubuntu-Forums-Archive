---
title: "Problems starting ubuntu"
date: 2010-08-08
forum: General Help
---

### Post by Nextgeneration on 2010-08-08
Recently I have had some problems starting linux, It gets to a part where it says it's loading grub and gives a countdown. I am using 10.4 ubuntu and it shows next a white ubuntu simbol It then starts doing a system scan and gives a persentage whne it gets to 33% it stops and says it can't mountall and that there is somthing wrong with the file system I can't get past this unless I don't evan let the scan start. I think somthing is a file is messed up but I have no idea what to do. Help wanted Please!:KS

---

### Post by X.Cyclop on 2010-08-08
What type of devices do you have installed on your computer? (NTFS, FAT32, mobile device, cd/dvd...) and what's the exact error that you get?

---

### Post by Nextgeneration on 2010-08-08
I got to the problem and wrote down everything.

mount of file system failed.5dbba8-a5f4-4do1-8dbd-203185960539
a maintenance shell will now be started
CONTROL-D will terminate this shell and re-try
root-tons-desktop~#exit
mountall start/starting
fsck from util-linux-ng 2.16
/dev/sdal contains a file system with errors, cheak forced
swapon: /dev/disk/by-uuid/768bo3af-5a95-42d6-bo27-99a7f23008fo:swapon failed: Device or resource busy
Mountall swapon  768bo3af-5a95-42d6-bo27-99a7f23008fo [855] terminated with status 255
mountall problems activating swap768bo3af-5a95-42d6-bo27-99a7f23008fo
File system cheaks are in progress(esc to cancel):
/dev/sdo1: unexpected inconsistencys: run fsck manually (i.e., without -a or -p options)
maountall: fsck / [853] terminated with statues 4
mountall: File system has errors:/
init:mountall main process (851) terminated with status 3
mount of file system failed

---

### Post by Nextgeneration on 2010-08-08
It will keep doing that as long as I try to start my computer if I let the checks run it will get to 33% and show that if I don't let it run it says there is an error and I should run checks.
I have a 77 gb filesystem linux Ext3(version 1.0) It's just a regular hard drive.I do have a cd/dvd player.

---

