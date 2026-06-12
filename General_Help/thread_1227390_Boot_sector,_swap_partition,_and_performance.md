---
title: "Boot sector, swap partition, and performance"
date: 2009-07-30
forum: General Help
---

### Post by Howard Kaikow on 2009-07-30
I've noticed that Ubuntu 9.04 performs much worse than did Ubuntu 7.04 on my multiboot Ubuntu/Windows+ system.

Could the swap partition be the problem?

When I installed 7.04, I had the swap partition on a 7200 rpm drive, and Ubuntu on a 10000 rpm drive. Having the partitions on a different drive is of course better, but how much better?

For 9.04, I created 4 partitions on the 10000 rpm drive, swap, /, /home, and /opt. Should I move the swap partition to one of the other drives (7200rpm)?

There is a bit over 3GB unused in the partition for one of my lesser used Windows OS. THe OS gets updated only for AV definitions, Office update, and Windows update, so 1GB may be enough for this.

Once I move the swap partition to another drive, I should make a new copy of the boot sector for the drive on which Ubuntu is installed. Of course, the copy of the boot sector I placed on the C drive (for multibooting) is using only the 1st 446 bytes, so the repartitioning should not affect anything, should it?

Currently, on the 10000 rpm drive, I have, in terms of 512 byte sectors:
2GB: swap, 4 208 967 sectors
8GB: /, 16 787 862 sectors
8GB: /home, 16 787 862 sectors
4GB: /Opt, 8 401 932 sectors

After I remove the 2GB, should I allocate the space to one of the other 3 partitions? If so, to which partitions?

---

### Post by DaithiF on 2009-07-30
Hi,
how much memory do you have installed?  If you are routinely swapping to disk then performance is going to be pretty poor no matter how fast your drive(s).  And so the better route to explore is either (a) adding more memory, or (b) reducing the load (memory) required by running less apps at one time.

Opening system monitor, what are your actual swap usage numbers?

thanks

---

### Post by Howard Kaikow on 2009-07-30
> **DaithiF said:**
> Hi,
how much memory do you have installed?  If you are routinely swapping to disk then performance is going to be pretty poor no matter how fast your drive(s).  And so the better route to explore is either (a) adding more memory, or (b) reducing the load (memory) required by running less apps at one time.

Opening system monitor, what are your actual swap usage numbers?

thanks

I am comparing what I saw with 7.04 and hat I now see with 9.04.

System memory is the same, and is at max for system.

In Windows, there is a difference if one has the pagefile on a different drive than the OS, I would expect the same with Linux.

THe bigget impact is going to be the renumbering of the partitions.

swap is on sdg5
/ is on sdg6
/home is on sdg7
/opt is on sdg8

REmoving the swap is going to change the numbers and this may necessitate my having to use the Super Grub Disk to rework the stuff I did in [Dual boot Windows/Linux using NTLDR ]("http://ubuntuforums.org/showthread.php?t=1222562").

For example, where I used 

```
$ sudo grub
type your password
grub> device (hd0) /dev/sdg
grub> device (hd3) /dev/sdg
grub> root (hd3,5)
grub> setup (hd0,5)
grub> quit
$ sync
$ reboot
```


and

```
sudo dd if/dev/sdg6 of=.media/MicronM/grubboot.lnx bs =512 
count=1

```

I expect that I would have to use SGD and use:

```
$ sudo grub
type your password
grub> device (hd0) /dev/sdg
grub> device (hd3) /dev/sdg
grub> root (hd3,4)
grub> setup (hd0,4)
grub> quit
$ sync
$ reboot
```


and

```
sudo dd if/dev/sdg5 of=.media/MicronM/grubboot.lnx bs =512 
count=1

```

---

### Post by michy99 on 2009-07-30
Actually, removing a partition doesn't seem to affect the /dev/ designations. Adding or removing a physical drive can, however, which is why it is recommended to use the UUID instead, which does not change.

---

### Post by DaithiF on 2009-07-30
Hi,
i would still like to know what your installed memory & swap usage levels are, in case swap partition isn't the cause of the perceived slow down in performance.  Moving your swap to a different partition isn't a trivial step (as the details that you have listed above illustrate!), so I think a little more diagnosis before taking that step might be prudent.
just a suggestion.
d

---

### Post by Howard Kaikow on 2009-07-30
> **michy99 said:**
> Actually, removing a partition doesn't seem to affect the /dev/ designations. Adding or removing a physical drive can, however, which is why it is recommended to use the UUID instead, which does not change.

The UUID may change, depending on the partitioning software used.

If the drive numbers do not change, then the task is a lot easier.

One issue is the crappy Partition Magic.

When I installed ubie 7.04, I pre-created the partitions with Partition Magic, no problem.

However, for 9.04, I created the partitions during the install using GParted. When I booted to Windows, Partition Magic said the drive was bad, tho Windows and Perfect Disk had no problems.

A few daze ago, I reset the MBRs with Windows Recovery Console, so maybe the PM crap is gone.

I'll try using Acronis Disk Director to redo the F drive to get the space for the swap partition, and to add the swap partition on HD2, and to remove  the swap on HD3.

Will ubie automatically detect the changed swap when I boot to ubie?

If not, how do I fix this?

If I can then still boot to ubie, then I'll backup everything.
For the time being, I can just let the unallocated space linger 
on hd3.

It will be interesting to see how Partition Magic reacts to all of this.

---

### Post by Howard Kaikow on 2009-07-30
> **michy99 said:**
> Actually, removing a partition doesn't seem to affect the /dev/ designations. Adding or removing a physical drive can, however, which is why it is recommended to use the UUID instead, which does not change.

Hmmm, but the Grub stuff I listed does not deal with the /dev designations, so I might have to do that anyway.

Maybe, my initial attempt should be to create another partition from within ubie using GParted and redesignate the swap partition to the other drive?

This still might not eliminate the grub issue, but may be a safer way to find out.

---

### Post by Howard Kaikow on 2009-07-30
> **DaithiF said:**
> Hi,
i would still like to know what your installed memory & swap usage levels are, in case swap partition isn't the cause of the perceived slow down in performance.  Moving your swap to a different partition isn't a trivial step (as the details that you have listed above illustrate!), so I think a little more diagnosis before taking that step might be prudent.
just a suggestion.
d

The installed memory is not relevant to my question, as it is at th max allowed and wa the same same for 7.04.

I'll boot to ubie now, and start the system monitor.

---

### Post by Howard Kaikow on 2009-07-30
I booted to ubie, where I am now.
As soon as I booted, I started System Monitor.
Also, the Update Manager started running.

I also started Firefox and Evolution.

The swap file is not even being used!

And there is lots of free memory, but CPU usage seems to be at 98-100%

It is also clear that the screen updates very slowly?

Should I see whether Radeon has Linux drivers and try to replace the Ubuntu drivers with those from Radeon? 

How do I replace such drivers?

If I install the Radeon drivers, will I have to re-install on sub sequent Ubuntu updates?

I did not see this problem with 7.04.

Also typing text is not slow, so it may just be a video driver issue?

---

### Post by DaithiF on 2009-07-31
ok good.  what process(es) are contributing to the 98-100% CPU usage.  In system-monitor go to the processes tab and sort by CPU.

---

### Post by Howard Kaikow on 2009-07-31
> **DaithiF said:**
> ok good.  what process(es) are contributing to the 98-100% CPU usage.  In system-monitor go to the processes tab and sort by CPU.

I believe that the high usage was due some start up stuff still running, plus I added Upate Manager, then Firefox and Evolution.

Memory use never got above about 271MB.

I then walked away for a few hours.

Memory use was down to around 177MB, and CPU usage had dropped, do not recall the numbers.

Went to ATI web site, for linux, there does not seem to be a driver for my card, so I'm stuck with whateve rUbunu includes.

If I wake up on time, I'll call AMD support later today. Of course, they are only in until 15:00 on Friday, so I might not wake up soon enough.

As I recall, this problem did not occur with ubie 7.04.
Ubie must have switched to some bloated generic video driver.

---

### Post by DaithiF on 2009-07-31
Hi Howard,
like with the swap partition it seems to me that you are perhaps jumping to a conclusion and a course of action that isn't supported by the facts.  

you've concluded that Ubuntu has switched to a 'bloated generic driver' and you're looking for a new one from ATI because:
(a) screen updating seemed slow
(b) typing speed at the time was ok, 
and from these two observations you have concluded that you have a video-driver problem?

But at the time CPU usage was 98-100%!  Of course screen updating is going to be slow if your CPU is maxed out.  Typing speed is irrelevant because the CPU power to process your keystrokes is infinitessimally smaller than the processing required to paint graphics on the screen.  So just because 'typing is ok' but screen updates are slow does not point to a bad video driver.

Rather than chasing down a new driver, I would suggest you first monitor CPU usage (in system monitor) over a few days, and pay particular attention when you perceive screen updating or general system performance to be slow.  If you see a pattern of particular applications hogging CPU then you'll have something concrete to investigate.

best of luck
D.

---

### Post by Howard Kaikow on 2009-07-31
> **DaithiF said:**
> Hi Howard,
like with the swap partition it seems to me that you are perhaps jumping to a conclusion and a course of action that isn't supported by the facts.  

you've concluded that Ubuntu has switched to a 'bloated generic driver' and you're looking for a new one from ATI because:
(a) screen updating seemed slow
(b) typing speed at the time was ok, 
and from these two observations you have concluded that you have a video-driver problem?

But at the time CPU usage was 98-100%!  Of course screen updating is going to be slow if your CPU is maxed out.  Typing speed is irrelevant because the CPU power to process your keystrokes is infinitessimally smaller than the processing required to paint graphics on the screen.  So just because 'typing is ok' but screen updates are slow does not point to a bad video driver.

Rather than chasing down a new driver, I would suggest you first monitor CPU usage (in system monitor) over a few days, and pay particular attention when you perceive screen updating or general system performance to be slow.  If you see a pattern of particular applications hogging CPU then you'll have something concrete to investigate.

best of luck
D.


The system monitor is the cause of the high CPU usage, likely in conjunction with the display issue, because of the frequent screen updating.

I did stumble upon one thing that may indicate a bug in Ubuntu 9.04 install.

I opened up Preferences | Display.
I noticed that the reesolution was set to the max 1600 x 1200.
I said, hmmm. maybe that's the problem.
So, I set the resolution to 1260 x 1024, which did improve  things.
Then I set the resolution back to 1600 x 1200, and found that things were not as slow as before.

The implication is that something was not set right, after the install, for the display properties.

FYI:

As I was typing this, I opened System Monitor and noticed that CPU utilization quickly jumped from 72% to 98-99%.

---

### Post by egalvan on 2009-07-31
> **Howard Kaikow said:**
> The UUID may change, depending on the partitioning software used.

UUID stands for Universally Unique IDentification.

Every time you create a partition, it recieves a unique ID string.
No two partitions ever have the same ID string.
No ID string is ever repeated.
In theory.

In practice.
The UUID tools allow one to read and write the UUID on any partition.

When you delete the partition and re-create it, the UUID changes.
you can copy the UUID first, then re-set it again once the partition is re-done.
This can save a lot of headaches with 'swap' UUID, since GRUB is not the only utility to use swap's UUID.

Personally, I changed to using LABEL instead of UUID.
My choice, it's easier FOR ME to use.
Your mileage may vary.

> 
One issue is the crappy Partition Magic.

When I installed ubie 7.04, I pre-created the partitions with Partition Magic, no problem.

However, for 9.04, I created the partitions during the install using GParted.
 When I booted to Windows, Partition Magic said the drive was bad, tho Will ubie automatically detect the changed swap when I boot to ubie?Windows and Perfect Disk had no problems.

Partitioning tools for *.nix have been migrating to a larger inode size.
Many 'foriegn' tools have not kept up.
For instance, Ext2-IFS ( [http://www.fs-driver.org/](http://www.fs-driver.org/) ) a driver to allow Windows to access ext2/3 is not updated yet.

> 
A few daze ago, I reset the MBRs with Windows Recovery Console, so maybe the PM crap is gone.
unless PM depends on specific features in it's own MBR, then this will not help.

> I'll try using Acronis Disk Director to redo the F drive to get the space for the swap partition,
 and to add the swap partition on HD2, and to remove  the swap on HD3.

**Will ubie automatically detect the changed swap when I boot to ubie?**

No. menu.lst, fstab and initrd.img.xxx needs updating.
> 
If not, how do I fix this?

There are posts and how-to's on this subject, but I don't have them to hand.


> If I can then still boot to ubie, then I'll backup everything.
For the time being, I can just let the unallocated space linger 
on hd3.

It will be interesting to see how Partition Magic reacts to all of this.

If you have an older version of Partition Magic, try updating.
It may solve some of the problems.

ErnestG
Countdown: five to go!

---

### Post by Howard Kaikow on 2009-07-31
> **egalvan said:**
> UUID stands for Universally Unique IDentification.

Every time you create a partition, it recieves a unique ID string.
No two partitions ever have the same ID string.
No ID string is ever repeated.
In theory.

In practice.
The UUID tools allow one to read and write the UUID on any partition.

When you delete the partition and re-create it, the UUID changes.
you can copy the UUID first, then re-set it again once the partition is re-done.
This can save a lot of headaches with 'swap' UUID, since GRUB is not the only utility to use swap's UUID.

Personally, I changed to using LABEL instead of UUID.
My choice, it's easier FOR ME to use.
Your mileage may vary.


I knew about UUID.

I've seen software that allows one to retain the old UUID.
Do not recall which software.



> **egalvan said:**
> Partitioning tools for *.nix have been migrating to a larger inode size.
Many 'foriegn' tools have not kept up.
For instance, Ext2-IFS ( [http://www.fs-driver.org/](http://www.fs-driver.org/) ) a driver to allow Windows to access ext2/3 is not updated yet.


The commercial products are Windows-centric.

I ASSuME that all will have newe versions for Windows 7, and will include support for more *ix file systems.


> **egalvan said:**
> unless PM depends on specific features in it's own MBR, then this will not help.

As long as I do not use PM to change/add partitions, the MBRs are fine as is.


> **egalvan said:**
> No. menu.lst, fstab and initrd.img.xxx needs updating.

There are posts and how-to's on this subject, but I don't have them to hand.

Turns out that me performance is not due to the swap file, rather it is due to the video driver and/or its settings.

I temporararily changed resolution from 1600 x 1200 to 1280 x 1024, then back to 1600 x 1200, and things improved. Still, slower than 7.04.


> **egalvan said:**
> If you have an older version of Partition Magic, try updating.
It may solve some of the problems.

I have the latest version of PM. PM 8 was created in May 2004. There have not, and there will be no, updates.

---

### Post by egalvan on 2009-08-03
> **Howard Kaikow said:**
> I knew about UUID.

I've seen software that allows one to retain the old UUID.
Do not recall which software.

This code will show all ID's attached to storage.
You can then copy it for later use
(I don't recall what command is used to write the UUID to a partition)
```
 sudo blkid
```

example (from one of my machines)
```
ernest@gx280:~$** sudo blkid**
[sudo] password for ernest: 
/dev/sda1: UUID="805424F85424F318" TYPE="ntfs" LABEL="gx280-xp" 
/dev/sda5: UUID="0933d680-d893-40fa-a01d-3c819f0b2ea3" TYPE="ext3" 
/dev/sda6: LABEL="puppy" UUID="3119f61a-7ab2-4b91-b9c8-44fa795dfae5" SEC_TYPE="ext2" TYPE="ext3" 
**/dev/sda7: TYPE="swap" LABEL="swap" UUID="7f9f938e-90da-4c2d-a75a-bd680b97aa4e" **
/dev/sdb1: LABEL="750-data1" UUD="ea49cca2-75fc-4082-a4d7-4bc040df5d8b" TYPE="ext3" 
ernest@gx280:~
```

Notice that some partitions have LABEL applied, which is what I use instead of UUID

In particular, note SWAP.
and this is how it looks in fstab
```
LABEL=swap            none            swap         sw          0  0  
```

very clean, and human-readable.

> 
I ASSuME that all will have new versions for Windows 7, and will include support for more *ix file systems.


Yeah, the *nix folks don't have the docs they need to easily write 
code for the MS-Windows side of things (reverse engineering is VERY time-consuming),
and too many MS coders are afraid of supporting Linux because they may receive a phone call with a Redmond WA prefix :(

> 
I have the latest version of PM. PM 8 was created in May 2004. There have not, and there will be no, updates.

I stopped using PM before that, so I wasn't aware it was no longer up-to-date.

---

