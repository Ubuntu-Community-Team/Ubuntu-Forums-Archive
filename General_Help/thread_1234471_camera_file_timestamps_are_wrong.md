---
title: "camera file timestamps are wrong"
date: 2009-08-07
forum: General Help
---

### Post by barthel on 2009-08-07
**Issue:** USB mounted FAT32 filesystems have the wrong timestamps on files. Offset appears to be UTC/Local conversion

**Background:**

Recently upgraded from Hardy to Jaunty. (64 bit editions)

I do not use f-spot or gphoto. I prefer to manually copy/delete the images. 

Yesterday I attempted to copy pictures from 2 cameras--and promptly ran afoul of the gvfs-gphoto2-volume-monitor bug.

After correcting that, I noticed that the timestamps were all 5 hours earlier than they should have been.  I checked both cameras to ensure they were still showing the correct time (US Central Daylight). I then compared photos I still had on the camera that I had copied prior to the jaunty upgrade. The camera copies were all timestamped 5 hours earlier than the hard drive copies. [Note that I never would have noticed (or have been able to confirm) this issue if I weren't copying files manually instead of relying on automated importing features.]

So, my question is: **what changed between hardy and jaunty that is causing timestamps on FAT32 volumes to be interpreted as UTC time instead of local time?** If it's a bug, I want to file it in the right place--and to be quite honest, between devfs, dbus, hal, gvfs, and more, I no longer know what subsystem is handling the actual identification and mounting. (When technology gets simpler for the end-user, it gets more complex under the hood...) On the other hand, if it's a new option I need to control, that's OK too. But my googles have not yielded any illumination to date.

TIA

---

### Post by jazgator on 2009-08-08
I just experienced the same issue while downloading images from my memory card.  When I reviewed the folders, much to my concern, files had been placed in folders for a different day.  The time shift for me was four hours, and the time in the image does not correspond to the time stamp in the memory card.  Does anyone have a solution for this issue> :confused:

---

### Post by aaron@roydhouse.com on 2009-09-06
I get the same problem with Ubuntu Jaunty 9.04 64 bit (all updates), it acts as if the timestamps on the SD card are UTC times.

---

### Post by lisati on 2009-09-06
I had a probably unrelated problem recently: the photos from a camera I hadn't use for a while ended up with a date of January 8, 2009 instead of 1 September 2009. Turns out I had set the clock in the camera incorreclty.

---

### Post by P4man on 2009-09-06
Not sure if Hardy used UTC. But perhaps you can work around this by setting your system to use local time:

```
gksudo gedit /etc/default/rcS
```

     >  # Set UTC=yes if your system clock is set to UTC (GMT)
      UTC=no

---

### Post by jazgator on 2009-09-07
Thanks for your feedback, this makes scence now since my system clock was being re-set when loading Ubuntu, then when I switched to Windows, the clock was off.
 
Now they are the same....:KS

---

### Post by barthel on 2009-09-08
> **P4man said:**
> Not sure if Hardy used UTC. But perhaps you can work around this by setting your system to use local time:

```
gksudo gedit /etc/default/rcS
```

I kept a copy of Hardy on another partition and compared the rcS files--UTC was set to yes on both.

However, the output of hwclock is 5 hours in the future--and I don't recall setting my system clock to UTC--so that might be the lead we're looking for. Thanks!

But resetting my system clock to UTC won't help drives maintained by external devices that keep local time instead of UTC...

I'll do a test later (have to leave for work) to see if setting UTC to "no" will affect how timestamps on external drives are interpreted.

---

### Post by dondos on 2009-09-08
If you observe the same files from Windows, do you see the correct timestamps?
Do you have the same problem with the files on a typical FAT32-formatted flash drive?
Does the problem affect all the files or only those modified / created during the winter months?

---

### Post by barthel on 2009-09-09
SOLVED!

Changing to "UTC=no" in /etc/default/rcS corrected the issue.

Here's my educated guess as to what is happening: When UTC=yes, timestamps on vfat are treated as if UTC were the filesystem's local time, so the appropriate conversion to local time is applied for displaying timestamps in user space. (In my example, subtracting 5 hours.) If UTC=no, then no conversion is done.

To confirm this guess, I next manually mounted the camera with the new "tz=UTC" option for vfat. The timestamps once again were off by 5 hours.

I next looked at the [patch]("http://lkml.org/lkml/2008/6/27/16") for the new "tz=UTC" option. I discovered that the kernel converts FAT timestamps to UTC using the sys_tz variable. (This is probably true for every format that uses local time instead of UTC for timestamps.) But this only works if the sys_tz is local time. 

So, despite the advantages (and sanity) of using UTC as the system time, local time should be the default. Every USB mass storage device that I've encountered in cameras, phones, and media players uses fat or vfat to be compatible with Microsoft. Sigh.

Heading over to launchpad...

---

### Post by barthel on 2009-09-10
Turns out that UTC=yes wasn't the culprit after all--but setting UTC=no is a valid workaround for the actual bug. Scott James Remnant identified the issue as settimeofday() not being called when UTC=yes. Here's the [bug report]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/426886").

---

