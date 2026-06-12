---
title: "Lost Partition Table/data"
date: 2010-10-12
forum: General Help
---

### Post by adzik on 2010-10-12
Hey all,

Have a slight partition/drive issue.
Prior to the weekend, I was using my system, everything was normal etc., and I was partitioning an external usb drive.
After all was done, disconnected the usb drive, and kept using my system for a while. Shut it down many hours later.
Came back today to use that laptop, and bang!, no system.
Booted up with a live usb, and checked the drive with the disk utility and it shows that my drive is "Free". No partitions, no system, nothin'.
I am led to believe that all the data is still there, although why it would nuke the partition table is beyond me.

Does anyone know how the system can be reverted back, if at all possible, and if not, the quickest way to recover files/directories? I am more peeved than concerned....:mad:

Thanks in advance.

---

### Post by srs5694 on 2010-10-12
I don't know why your disk's partitions got wiped, unless perhaps you intended to wipe the partitions on the USB drive at some point but accidentally worked on your internal disk instead. You wouldn't notice this error immediately because the kernel keeps the old partition table in memory if you edit the partition table on disk.

The usual solution to the problem is to use [TestDisk,](http://www.cgsecurity.org/wiki/TestDisk) which can scan a hard disk for filesystem signatures and rebuild a partition table using what it finds. You might need to re-install your boot loader when this finishes.

Going forward, you can back up your partition table and keep a copy on a USB flash drive or another computer. I've got directions at the bottom of [this page.](http://nessus.rodsbooks.com/gdisk/mbr2gpt.html) (Ignore everything else; just read the "Final Conversion Thoughts" section.)

---

### Post by adzik on 2010-10-13
Well, I haven't a clue as to why the partition table was wiped out, but ran TestDisk, and recovered the partition table fully.
Had to use [[COLOR="Navy"]SuperGrubDisk[/COLOR]]("http://www.supergrubdisk.org/") to boot into the system (since grub was gone).
System looks good. Everything is accounted for and like it never happened.
I'll be backing up the table just in case...

Now, the next step is reinstalling grub. This I am not familiar with. Any guidance on recovering grub2 bootloader?

Thanks for the tips srs5694. Big time appreciated.

---

### Post by P4man on 2010-10-13
Grub was probably installed on the removable drive?
Can you run bootinfoscript and post the results here?
Here is how:
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by srs5694 on 2010-10-13
Once you've booted using Super GRUB Disk, you should be able to re-install GRUB by typing "sudo grub-install". It may be necessary to precede that command with "sudo update-grub" if your partition numbers have changed.

---

### Post by adzik on 2010-10-14
[QUOTE=P4man]Grub was probably installed on the removable drive?
Can you run bootinfoscript and post the results here?
Here is how:
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)[/QUOTE]

I was unable to run this script, no output given as to reason why it wouldn't run. 

[QUOTE=srs5694]Once you've booted using Super GRUB Disk, you should be able to re-install GRUB by typing "sudo grub-install". It may be necessary to precede that command with "sudo update-grub" if your partition numbers have changed.[/QUOTE]

With this, grub-install has no effect, meaning it outputs the grub-install help only. Already performed update-grub, which indicated it was successfully, but still did not recover the grub2 bootloader.
obviously, it's there in the partition itself, since I am able to boot using SuperGrubDisk.

As a reference, here is the partition table output from fdisk -l

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          36      289138+  83  Linux
/dev/sda2              37        9656    77272650   83  Linux
/dev/sda3            9657        9729      586372+  82  Linux swap / Solaris
```


I appreciate your efforts, guys.

---

### Post by srs5694 on 2010-10-14
> **adzik said:**
> With this, grub-install has no effect, meaning it outputs the grub-install help only.

Oops. Sorry. That should be:

```

sudo grub-install /dev/sda

```

---

### Post by adzik on 2010-10-14
Performed a grub-install on /dev/sda, and it worked perfectly. It would explain why my earlier attempts weren't working... I was using /dev/sda1.
Anyway, the bootloader is back. 
Thanks for that tip **srs5694**.
Now, if I could only track down why the partition table was removed in the first place, that would be good.  I think from now on I'll be sticking to the terminal for disk functions.  Everytime I've use the gui disk tools in ubuntu, I've lost data in some way or another. Maybe I'm just clumsy with the trackpad or something.

Thanks again all!

---

