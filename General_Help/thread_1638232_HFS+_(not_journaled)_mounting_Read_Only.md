---
title: "HFS+ (not journaled) mounting Read Only"
date: 2010-12-05
forum: General Help
---

### Post by omega0 on 2010-12-05
I have an eSATA drive connected to my laptop running Ubuntu 10.04.  The filesystem on the drive is HFS+, but I disabled journaling before connecting it to the Ubuntu laptop.  I was able to write to the drive in Ubuntu for a few weeks.  Yesterday I plugged in my MagicJack to the Ubuntu computer, attempting to get it to work with VMWare Player and Windows XP.  That did not work, so I unplugged the MagicJack.  But ever since doing that this drive will only mount as read only, but I need to write to it.  The MagicJack does mount as a mass storage device, but I am unsure how to remove remnants of it, if that is what is causing the problem.

I attached a screenshot of the mtab, since it is mounted in media and disk utility showing the drive.

Thanks

---

### Post by omega0 on 2010-12-05
Update:

I installed a clean version of Ubuntu 10.10 on this laptop.   All the HFS+ drives are now mounting read-only.  I cannot figure this out.  I installed the following packages:

hfsplus
hfsutils-tcltk
libhfsp0
hfsprogs
hfsutils

and restarted the computer, still mounting as read-only.  Please Help?

---

### Post by oceanstate8 on 2010-12-19
I am having a similar problem in 10.10.  I use a non-journaled HFSplus partition as /home.  It has worked fine for months, until yesterday it began mounting as read only.  I verified that my settings in fstab were still correct.  Why this would suddenly stop working, I'm not sure.

---

### Post by trojanfoe on 2011-01-10
Did any of you guys figure this out?  I want to exchange large amounts of data between by Ubuntu Server (10.10, x64) and my MacBook Pro.  I cannot find a decent ext2 driver for Mac OS so I'd like to use HFS+ and it mounts readonly (It's a case-sensitive unjournaled filesystem).

---

### Post by srs5694 on 2011-01-10
First, examine the last few entries of the kernel ring buffer with dmesg, as in:

```

$ **dmesg | tail**
[1036945.505958] hfs: write access to a journaled filesystem is not supported, use the force option at your own risk, mounting read-only.

```

I've truncated this output, but it shows what happens when you try to mount a journaled HFS+ volume read/write. It's conceivable that the disk's journal has been activated without your knowledge, or there might be some other problem that will show up in the dmesg output.

Second, try booting into OS X and using Disk Utility to check the partition. It's possible it wasn't cleanly unmounted and this is causing Linux to be conservative and give you read-only access to the partition.

---

### Post by trojanfoe on 2011-01-11
> **srs5694 said:**
> First, examine the last few entries of the kernel ring buffer with dmesg, as in:

```

$ **dmesg | tail**
[1036945.505958] hfs: write access to a journaled filesystem is not supported, use the force option at your own risk, mounting read-only.

```

I've truncated this output, but it shows what happens when you try to mount a journaled HFS+ volume read/write. It's conceivable that the disk's journal has been activated without your knowledge, or there might be some other problem that will show up in the dmesg output.

Second, try booting into OS X and using Disk Utility to check the partition. It's possible it wasn't cleanly unmounted and this is causing Linux to be conservative and give you read-only access to the partition.

If this was StackOverflow, I'd be pressing the 'tick' next to your answer right now!  I have exactly that output in the kernel log:

```
[  670.580870] hfs: write access to a journaled filesystem is not supported, use the force option at your own risk, mounting read-only.

```
I will remove the journal and try again.  Do you know how the journal becomes active without consent like this?

-A

---

### Post by srs5694 on 2011-01-11
I know that the journal can be activated by certain OS X disk utilities. (I think there's an option for it in OS X's GUI Disk Utility program, but my OS X systems are shut off at the moment so I can't easily check it.) There's probably an option for this in some text-mode tools, too. Thus, my guess is that it was accidentally activated, either by user error (an unintended click in a check box) or by a buggy script that does disk check activity. That's just a guess, though.

---

### Post by trojanfoe on 2011-01-11
We'll it seems to be working - my Linux Server has spent all day writing files to the HFS+ filesystem and hasn't finished yet.  There are no errors so far, so I assume it will work.

Many thanks for your help!

-A

---

