---
title: "ubuntu 9.04 manual fsck help!!!"
date: 2010-01-01
forum: General Help
---

### Post by funkyguy4000 on 2010-01-01
Okay so I am using my brothers laptop and i am not an administrator on it.  He moved away and let me use it.  I started it up and it says something about it not shutting down properly and it started checking for errors on the disk.  It stopped at 1% didn't go anywhere i guess.  stopped while it was checking dev1/sda1 and said I needed to run a manual fsck.

Now i am not an ubuntu user at all, I am an old fashioned windows user.  
So i was windering how do i fix this!?!?

I know about grub but thats basically it.  I have like no ubuntu smarts whatsoever.

Thanks in advance!

---

### Post by jbrown96 on 2010-01-02
Usually you can press "escape" when the scan first starts to skip it. However, if there's actually something wrong with the disk or it got corrupted, then you may need to do some additional work.

You say that you know about grub, so open the menu when it first boots. Highlight the top Ubuntu entry (most recent kernel version), and press "e". This will allow you to edit the entry. There is one line that is very long, and at the end is "splash", change it to "nosplash" (no quotes), then boot. See if you can see any other error messages.

---

### Post by funkyguy4000 on 2010-01-02
okay so i did the nosplash thing and i still got the same error.

from what i can see on my screen i see

[63.486237] ata1.00:status:{DRDY ERR}
[63.486270] ata1.00:error:{UNC}
[63.508980] end_request: I/O error, dev sda, sector 2097231
[63.509017] Buffer I/O error on device sda1, logical block 262146
Error reading block 262146 (Attempt to read block from filestystem resulted in short read) while getting next inode from scan.

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
                            (i.e., without -a or -p options)
fsck died with exit status 4
[fail]

((wierd red star thing)) An automatic file system check (fsck) of the root filesystem failed. A manual fsck must be performed, then the system restarted. The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.

((wierd yellow star thing)) The root filesystem is currently mounted in read-only mode. A maintenance shell will now be started.  After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system. 

Give root password for maintenance
(or type control-D to continue): _



Now i don't have the password, b/c i'm not an admin.  so how would I run the fsck manually without the -a or -p parameters?  And where would i stick the coding?

---

### Post by prshah on 2010-01-02
> **funkyguy4000 said:**
> 
Now i don't have the password, b/c i'm not an admin.  so how would I run the fsck manually without the -a or -p parameters?  And where would i stick the coding?

You can choose "recovery mode" from the grub menu, to get to a maintenance menu. Choose "Root Terminal" (or similar option) to land up in a superuser (admin) command prompt. It should not prompt you for a password. 

If this fails, you can boot off a live CD, then open a Terminal (Applications-Accessories-Terminal) and perform fsck as detailed below. If you are using the live CD route, please stick "sudo " in front of all the below commands. It will not prompt for a password.

From this command prompt, you can run fsck manually with the command```
fsck /dev/sda1
```.

It may make more sense to use this command ```
fsck [color=red]-y[/color] /dev/sda1
``` but there is a small (minimal, really) risk of damage to data (but I don't see how you can avoid this risk as a newb anyway).

If you suspect there are bad sectors, you should use ```
fsck -y -c /dev/sda1
``` but this will take a much longer time to complete since it actually checks the physical structure of the hard disk. Same rules of risk to data apply.

You do this at your own risk. Please heed all warnings from fsck (at least don't ignore them outright), especially warnings about running fsck on a mounted filesystem.
Please post back if you run into problems or want more information.

---

### Post by funkyguy4000 on 2010-01-02
i did the fsck -y /dev/sda1 thing and it came up with a box with a few options
I went down to fsck and pressed enter and it started saying the samee things as it was before

```
[some funky number] ata1.00: status: {DRDY ERR}
[bigger funky number] ata1.00: error: {UNC}
[even bigger #] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[even Bigger #] ata1.00: BMDMA stat 0x25
[even bigger #] ata1.00: cmd c8/00:08:5f:31:24/00:00:00:00:00/e0 tag 0 dma 4096 in
[even bigger #]            res 51/40:05:62:31:24/00:00:00:00:00/e0 Emask 0x9 (media error)
```

and every once in a while after the {UNC} code it would say

```
[big number] end_request : I/O error, dev sda, sector 2371938
[big number] buffer I/O error on device sda1, logical block 296484
Error reading block 296484 (Attempt to read block from filesystem resulting in short read) while reading indirect blocks of inode 65596.  Ignore error<y>? (i said yes)

Force rewrite<y>?  
```

I always said no for the rewrite because i didn't want to lose any data my brother may have on here. 

It always has the error with the inode 65596 but a different block.

What would happen if i said yes to rewrite? And what do these mean.

---

### Post by funkyguy4000 on 2010-01-02
whoops there was a duplicate post here. refer to the one above ^^^^^^^^^^^^^^^^^^

---

### Post by prshah on 2010-01-02
> **funkyguy4000 said:**
> ```
<snip>res 51/40:05:62:31:24/00:00:00:00:00/e0 Emask 0x9 [color=red](media error)[/color]
```

```
Force rewrite<y>?  
```

What would happen if i said yes to rewrite? 

Your HDD is probably physically damaged. Forcing a rewrite (everytime) seems to be your only option and that too may not work out.

You will probably lose some data by forcing a re-write. But consider that about 10,000 ~ 20,000 files belong to the operating system, and then imagine that chances that one of YOUR files is getting damaged. Unlikely; but not impossible.

The best I can suggest is that you take a backup (as much as possible) of your files, and then try the force rewrite.

You might probably have to change your hard disk soon.

---

### Post by funkyguy4000 on 2010-01-05
alright so basically I was able to get to that manual fsck rewrite prompt again and when I said yes to the force rewrite it deleted a few files which were unneeded. and then i fiddled around a little bit.

Now i can log in but i can't graphically log in.  It gives me this error about my session lasting less then 10 seconds.

I posted a new thread about it here

[http://ubuntuforums.org/showthread.php?t=1373505](http://ubuntuforums.org/showthread.php?t=1373505)

---

### Post by kingtaurus on 2010-01-05
You probably should run (if this crops up in the future):
```

fsck -y -c -c /dev/sda1

```
The extra **-c** is so that the test use a non-destructive read-write check on the disk (this takes longer - but could find additional bad sectors of the drive, these will be added to the bad_block list and **will not** be used in the future.).

---

### Post by kingtaurus on 2010-01-05
<snip>

---

### Post by dcstar on 2010-01-05
> **kingtaurus said:**
> You probably should run (if this crops up in the future):
```

fsck -y -c -c /dev/sda1

```
The extra **-c** is so that the test use a non-destructive read-write **check on the disk **(this takes longer - but could find additional bad sectors of the drive, these will be added to the bad_block list and **will not** be used in the future.).

It does **not** check "the disk", it checks the particular filesystem that has been allocated space on the disk.

Enable SMART in the BIOS and install the **smartmontools** & **smart-notifier** packages and set up a job for the disk to test itself for any bad blocks.

---

### Post by kingtaurus on 2010-01-05
> **dcstar said:**
> It does **not** check "the disk", it checks the particular filesystem that has been allocated space on the disk.

Enable SMART in the BIOS and install the **smartmontools** & **smart-notifier** packages and set up a job for the disk to test itself for any bad blocks.

Umm ... according to the man pages of badblocks (which is used by fsck.ext3):
Non-destructive read-write -
```

Use non-destructive read-write mode.  By  default  only  a  nondestructive  
read-only  test  is  done.  This option must not be
combined with the -w option, as they are mutually exclusive.

```

Destructive read-write -
```

Use write-mode test. With this option, badblocks scans  for  
bad blocks  by  writing  some  patterns  (0xaa, 0x55, 0xff, 0x00) 
on every block of the device, reading every block and comparing the 
contents. This  option may not be combined with the -n option, as they 
are mutually exclusive.

```

Thus: **-c -c** does exactly as mentioned specified. It test reading and writing to a block device (not to the file system).

---

### Post by dcstar on 2010-01-05
> **kingtaurus said:**
> Umm ... according to the man pages of badblocks (which is used by fsck.ext3):
Non-destructive read-write -
```

Use non-destructive read-write mode.  By  default  only  a  nondestructive  
read-only  test  is  done.  This option must not be
combined with the -w option, as they are mutually exclusive.

```

Destructive read-write -
```

Use write-mode test. With this option, badblocks scans  for  
bad blocks  by  writing  some  patterns  (0xaa, 0x55, 0xff, 0x00) 
on every block of the device, reading every block and comparing the 
contents. This  option may not be combined with the -n option, as they 
are mutually exclusive.

```

Thus: **-c -c** does exactly as mentioned specified. It test reading and writing to a block device (not to the file system).

man badblocks:
badblocks is used to search for [B]bad blocks on a device (usually a  disk
partition[/B]). device  is  the  special file corresponding to the device
e.g /dev/hdc1).

Where do you think it is going to "write" any bad block info on a non-partitioned device area?

---

### Post by kingtaurus on 2010-01-06
> **dcstar said:**
> man badblocks:
badblocks is used to search for [B]bad blocks on a device (usually a  disk
partition[/B]). device  is  the  special file corresponding to the device
e.g /dev/hdc1).

Where do you think it is going to "write" any bad block info on a non-partitioned device area?

Sorry, I misspoke, I should have said partition or device (instead of disk). But it **doesn't** just check the **filesystem**. It checks the underlying physical device (only the CHS of the associated formatted partition - but it does check reading and writing to the device). However my point still stands - it checks the physical device in addition to the **filesystem**.

A check with **-c -c** can provide additional badblocks beyond just a **-c** check.

We should take this discussion elsewhere - we are distracting from the original posters problems.

---

