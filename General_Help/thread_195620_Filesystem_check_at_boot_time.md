---
title: "Filesystem check at boot time"
date: 2006-06-13
forum: General Help
---

### Post by eth on 2006-06-13
Hi all, 
at every boot on my machine, running Dapper, it checks all the fs found. In particular, it checks 2 Fat32 partition and it finds a difference between actual and the backup (something like 00-64/01) but it tells me that it's not going to fix this. 
Both the partition works great anyway, I'd like to know then what's wrong AND if I can get rid of that annoying fscheck at every boot. 
Uh, one more thing: once, and only once, I found a 1.5Gb file named pagefile.sys in one of them, but I deleted it and it didn't come back.

---

### Post by dabang on 2006-06-13
It's a normal procedure checking the filesystems at boot time. the difference you are mentioning is about the boot sector and it's backup. I actualy don't know what it means, but I think it's nothing to worry about, as it shows up in every debian-based distro I know.
"pagefile.sys" (as the name says) is the pagefile for windows, where it puts all data which doesn't fit into RAM, like Linux swap drive. The file should be recreated the next time you boot into windows again.

---

### Post by eth on 2006-06-13
I knew about the .sys windows ram extension, but there's no window installed...

...anyway, the matter is that it always exits usplash, and get in text mode...AND it takes some time to check it! 
I had had no problem of this kind with Breezy (5.10)...

---

### Post by dabang on 2006-06-14
Oh, then I misunderstood your posting. "Checking Filesystems..." is normal at bootup, but if there's a complete FS check leaving bootsplash, it's different.
You could look at /etc/fstab. The number in the 6th column determins how the FS is checked. If it's an "0" it won't be checked at all.

As about the pagfile.sys: I don't know of any distribution crearting such file...

---

### Post by hayalci on 2006-06-18
Yes, by default the ubuntu installer placed "1"s all over /etc/fstab, and I wait about a minute for the checks, thinking why. No other distro I saw before did this.
Thanks dabang for the tip.

Pointer to the clueless and maybe a helper for someone: /etc/fstab file holds the info about filesystems on your disk. To disable checking of each partition on bootup, open the /etc/fstab file as root ( you can use "sudo nano -w /etc/fstab" on the command line or use  "run  as different user" from the menu [ it is not present on default menu, use the menu editor ] and run "gedit /etc/fstab" as root.  Replace the "1"s at the end of lines with "0"s, do not mess with the spaces or new lines. Your bootup time will be enhanced greately.

---

### Post by xenomorph99 on 2006-06-18
Hi,

I haven't noticed a filesystem check at bootup but I did get one today as it was the '30th' time that the Linux partition had been mounted. 

Like the original poster, I did get a message saying there were 7 differences between the boot sector record and it's backup but that they wouldn't be automatically fixed.

So, are these 'differences' actually 'errors' and is it necessary to run a periodic 'flush out' to get rid of such problems?

Ta,
Xeno

---

### Post by hayalci on 2006-06-19
The check on 30th boot is no problem, and normal behaviour. Mine was getting checked on "every" boot until I removed "1"s.


Boot sector backup mismatch is probably because of the bootloader installation of ubuntu. 

Using dosfsck command on the terminal you can fix this, but I have not tested (answered no action) because I want to first test if wind0ze boots properly, then I may try fixing using dosfsck.

```
root@piton:/etc/acpi/events# umount /dev/hda1
root@piton:/etc/acpi/events# dosfsck /dev/hda1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  430:4e/44, 431:54/69, 432:4c/73, 433:44/6b, 434:52/20, 435:20/76, 437:6b/79
  , 438:73/61, 439:69/20, 440:6b/62, 441:ff/61, 442:0d/73, 443:0a/6b
  , 444:44/61, 445:69/20, 446:73/6f, 447:6b/72, 448:20/74, 449:68/61
  , 450:61/6d, 451:74/20, 452:61/63, 453:73/69, 454:69/6b, 455:ff/61
  , 456:0d/72, 457:0a/69, 458:42/6e, 459:61/2e, 460:73/ff, 461:6c/0d
  , 462:61/0a, 463:74/44, 464:6d/69, 465:61/73, 468:69/68, 469:63/61
  , 470:69/74, 471:6e/61, 472:20/73, 473:74/69, 474:75/ff, 475:73/0d
  , 476:61/0a, 477:20/42, 478:62/61, 479:61/73, 480:73/6c, 481:69/61
  , 482:6e/74, 483:0d/6d, 484:0a/61, 485:00/6b, 486:0d/20, 487:0a/69
  , 488:00/63, 489:00/69, 490:00/6e, 491:00/20, 492:00/74, 493:00/75
  , 494:00/73, 495:00/61, 496:00/20, 497:00/62, 498:00/61, 499:00/73
  , 500:00/69, 501:00/6e, 502:00/0d, 503:00/0a, 506:ba/cd, 507:c8/db
1) Copy original to backup
2) Copy backup to original
3) No action
? 3
/dev/hda1: 52642 files, 1102221/1707574 clusters
root@piton:/etc/acpi/events#

```

---

### Post by GozzoMan on 2006-06-25
Trying to fix this same problem with dosfsck as suggested, if I choose the 1 or 2 option I obtain "Leaving filesystem unchanged" and following run of dosfsck keeps reporting the problem.

I was using sudo and the filesystem was unmounted.

Any idea on why dosfsck is unable to operate on the fs as it seems?

---

### Post by hayalci on 2006-06-26
Well, the dosfsck man page states that;

>  If -a and -r are absent, the file system is only checked, but not repaired. 

and -r worked for me :)

---

### Post by GozzoMan on 2006-06-29
Well, d'oh! #-o

Thanks, hayalci, this way it worked without a fuss. :)

---

### Post by hayalci on 2006-06-29
You're welcome :)

---

### Post by tassoman on 2006-07-16
```

tassoman@lumaco:~$ sudo dosfsck -a -r /dev/sda1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  430:4e/52, 431:54/69, 432:4c/6d, 433:44/75, 434:52/6f, 435:20/76, 436:6d/65
  , 437:61/72, 438:6e/65, 439:63/20, 440:61/73, 441:6e/75, 442:74/70
  , 443:65/70, 444:ff/6f, 445:0d/72, 446:0a/74, 447:45/69, 448:72/2e
  , 449:72/ff, 450:6f/0d, 451:72/0a, 452:65/45, 453:20/72, 454:64/72
  , 455:69/6f, 456:73/72, 457:63/65, 458:6f/20, 459:ff/64, 460:0d/69
  , 461:0a/73, 462:50/63, 463:72/6f, 464:65/ff, 465:6d/0d, 466:65/0a
  , 467:72/50, 468:65/72, 469:20/65, 470:75/6d, 471:6e/65, 472:20/72
  , 473:74/65, 474:61/20, 475:73/75, 476:74/6e, 477:6f/20, 478:20/74
  , 479:70/61, 480:65/73, 481:72/74, 482:20/6f, 483:72/20, 484:69/70
  , 485:61/65, 486:76/72, 487:76/20, 488:69/72, 489:61/69, 490:72/61
  , 491:65/76, 492:0d/76, 493:0a/69, 494:00/61, 495:00/72, 496:00/65
  , 497:00/0d, 498:00/0a, 506:bd/c2, 507:cc/d1
1) Copy original to backup
2) Copy backup to original
3) No action
?

```

Wich answer!? o_O?

---

### Post by lzap on 2006-07-16
1 should be fine, it overwrites the backup.

---

### Post by tassoman on 2006-07-17
I think so, the problem were started when I've re installed Ubuntu dapper from skratch over Kubuntu 5.10

---

### Post by golem3 on 2007-01-25
You we are suggesting that 

sudo gedit /etc/fstab

and edit the last value for the primary (hda1) such that 1 becomes 0.

THanks a lot if this works!

---

### Post by dcstar on 2007-01-25
> **golem3 said:**
> You we are suggesting that 

sudo gedit /etc/fstab

and edit the last value for the primary (hda1) such that 1 becomes 0.

THanks a lot if this works!

That would stop the auto fsck of that drive when it is mounted, this is basically insane (if this is your "/" partition) because you will then not be checking for any corruption, and you will run the risk of losing your whole system one day.

---

### Post by phersotty on 2007-01-28
Hello Ubuntu world !!

It looks like this thread is a bit old, but I think my question falls under this topic.  I've recently restored my Sony VGN A250 laptop back to the factory settings.  Then I revved it up with some Linux kung fu.:guitar:   It is now a triple booting laptop with XP Home, Beryl enabled Kubuntu, and GeexBox for that instant Media player feature they are putting on all the new laptops.  So here is my problem:  When I try to show off to my friends how much better and revitalized my laptop is fsck throws out a scary non gui message about my file systems not being in check.  If I type exit then everything loads according to plan.  I have tried changing  the 2 to a 0 in my fstab for the partition in question but then it won't boot at all.   Any suggestions ??  

Here is the log file that is created in /var/log/fsck/checkfs
> Log of fsck -C -R -A -a 
Sun Jan 28 19:25:00 2007

fsck 1.39 (29-May-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda3: 42 files, 728/1278928 clusters
fsck.ext3: Unable to resolve 'UUID=0c0436d4-ab75-11db-9a8e-c1d916156abb'
fsck died with exit status 8

Sun Jan 28 19:25:01 2007
----------------
  

and here is my current /etc/fstab

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7 geexbox
UUID=1499796e-96ab-4ae0-b96a-369d6d6fbdf5 /               reiserfs notail          0       1
# /dev/hda1 sony recovery partition
UUID=220CFF700CFF3D7B /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2 xp home
UUID=1E3C2A403C2A12F7 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3 fat32 partition for sharing data
UUID=2833-8105  /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6 kubuntu
UUID=0c0436d4-ab75-11db-9a8e-c1d916156abb /media/hda6     ext3    defaults        0       2
# /dev/hda5 swap
UUID=71d4a0e6-11bb-427b-a8c2-7a24ce02cd0f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0



---

### Post by hayalci on 2007-02-05
If you have reformatted your /dev/hda6, it cannot find the relevant UUID, because IDs change with formats. Try writing /dev/hda6 instead of the UUID or learn the new id with vol_id program.

---

### Post by the_mouse on 2007-02-07
If I set 0 option for filesystem check for fat32 partition, is there any risk of losing data? Will fsck check the filesystem every 30 days if there is 0 option?

---

### Post by mcduck on 2007-02-07
> **the_mouse said:**
> If I set 0 option for filesystem check for fat32 partition, is there any risk of losing data? Will fsck check the filesystem every 30 days if there is 0 option?

No, it wont ever run for partitions with '0'.

But you can use '2' instead. '1' should only be used for /, for other partitions you can choose between '2' and '0'.

Anyway, I've turned fsck off for FAT & NTFS partitions. I haven't had any problems, and anyway I'm not sure if fsck really could do anything to those partitions even if I used it..

---

### Post by the_mouse on 2007-02-08
What does the '2' option do?

---

