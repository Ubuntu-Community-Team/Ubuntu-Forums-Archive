---
title: "Floppy Disk won't work"
date: 2011-01-08
forum: General Help
---

### Post by RogerDavis on 2011-01-08
I'm trying to read contents of a floppy disk, can't even find the disk, much less contents.  

Help?!?

---

### Post by 3602 on 2011-01-08
I believe that due to the age of 1.44M disks, such hardware aren't even supported. It may be better to find a service to pull the data from your disks into CD-R's or a USB storage device.

---

### Post by ron999 on 2011-01-08
[COLOR="White"]>>>>>>>>>>>>>[/COLOR]

---

### Post by nerdy_kid on 2011-01-08
> **ron999 said:**
> Hi
I'm using Karmic. Maybe it's the same with Lucid.
To access floppies I had to do this:-
**Comment out the /dev/fd0 entry in the /etc/fstab file and reboot.**

Then to mount the floppy use:-

```
sudo mount /dev/fd0 /media/floppy0
```


Use [FONT="Courier New"][SIZE="5"]gksudo nautilus[/SIZE][/FONT] to copy files to/from the floppydisk.

To unmount use:-

```
sudo umount /dev/fd0
```

this

you actually might have to do

sudo mount -o loop /dev/fd0 /media/floppy0

for some reason ubuntu wont mount them unless I use loop back.

---

### Post by Geokimbo on 2011-01-13
I have the same problem and a conventional mount using 

mount /dev/fd0 /media/floppy0 

does not work for me. 

Nerdy_kid's  -o loop option does however work but I can not then unmount in order to read another floppy. I get an error telling me that the device is not mounted. So far the only way I have been able to read more than one floppy is to do a reboot after each read - OK I'm new to this - I know there has to be a more elegant solution.

The floppy used to work quite happily under 8.04 and 8.10. I don't recall if I used it through the 9s but it does not appear to work properly under 10.

I'm just trying to recover some old archived data. The next step will be to pull an old Win2k machine out of storage and use it - I may have to anyway as I've found some old 5.25" floppies as well and I seem to recall there was no support for them under Ubuntu.

---

### Post by csacpt on 2011-01-13
Try this thread, it had to do with a package version on Lucid for me.

[http://ubuntuforums.org/showthread.php?t=1511446](http://ubuntuforums.org/showthread.php?t=1511446)

---

### Post by RogerDavis on 2011-01-14
I find I can use Disk Utility to mount and unmount my LS-120, which will read a common floppy also, but Disk Utility won't work for the floppy, even though the floppy is shown as a device ( /dev/fd0 ).

But the volume has to be manually mounted, then manually unmounted before it will eject.  How do I fix this?

So my practical problem is solved, but my "dammit, it should work" for the true floppy isn't.  Why would it be shown in the utility, but be unserviceable?!?  It shows "no media detected, connection unknown, SMART status - not supported"

---

### Post by Geokimbo on 2011-04-01
I tried the suggestions on the thread pointed to by CSACPT but still no joy so far the only luck I have had is using the -o loop option which unfortunately only works once before I have to reboot in order to unmount and then remount the next floppy.

The arguments about using USB sticks are all valid if the intention is to replace floppies. They do not address the problem of what to do with legacy data from the last century. The hardware still works I just need a working driver for it.

Cheers
Kim

---

### Post by plucky on 2011-04-01
> **Geokimbo said:**
> I tried the suggestions on the thread pointed to by CSACPT but still no joy so far the only luck I have had is using the -o loop option which unfortunately only works once before I have to reboot in order to unmount and then remount the next floppy.

The arguments about using USB sticks are all valid if the intention is to replace floppies. They do not address the problem of what to do with legacy data from the last century. The hardware still works I just need a working driver for it.

Cheers
Kim

Have you tried from a terminal ```
udisks --mount /dev/fd0
```

The solution in that link is only if you are running Lucid and can downgrade the udisks package.

Good Luck

---

### Post by grahammechanical on 2011-04-01
Perhaps you do not have permission to use a floppy drive. I do not have a floppy drive installed and the custom privileges that I were given when I installed Ubuntu do not include using a floppy drive.

Go to System>Administration>User and groups. Select Advance settings and User privileges. You may find that the Use floppy drives box is not ticked. You may need to reboot.

Regards.

P.S. Disk Utility on my machine does have a heading for a floppy drive although I do not have one installed.

---

### Post by RogerDavis on 2011-04-04
I've tried all the suggested methods for 10.04 LTS, no luck.

When Ubuntu is touted as the best operating system for older systems with small memory, it should be kept in mind that almost all older systems have floppy drives.  Look down at foot, observe bullet hole...

It is essential to have EASY, AUTOMATIC mounting of all installed drives.

---

### Post by bigfut on 2011-08-14
Sometimes it is knowing where to mount it,,,my USB floppy is actually /dev/sdf . Gave myself permission to use floppy in System/Administration/Users and Groups. Then I had followed someone's advice to comment out the fd0 in etc/fstab and re-boot because my Motherboard doesn't have a floppy interface.  So now I just mount /dev/sdf and there it is.  I now need to figure out how to automount and all  will be well. Hope this helps.

---

