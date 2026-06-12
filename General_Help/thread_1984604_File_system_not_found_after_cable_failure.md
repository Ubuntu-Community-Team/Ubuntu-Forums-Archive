---
title: "File system not found after cable failure"
date: 2012-05-22
forum: General Help
---

### Post by Anthem on 2012-05-22
Hey gang.  I haven't posted on here in quite a while.

My wife's laptop (Dell Vostro V13) had a hard drive cable go bad, and when I tried to recover the data I've run into some snags.  It was running a Xubuntu 11.10 install, so I'm assuming EXT4.  The drive itself is a 30Gb OCZ Vertex (solid state).

- The BIOS can see the physical drive, but GNOME can't find it when booting from USB.

- Booting UbuntuRescueRemix allows me to try testdisk, which does see a partition.  Unfortunately, the partition has no file system.  Using TestDisk's analyze feature does me no good; it cannot find a partition even when using "Deeper Search."

- I've tried recovering the partition based on backup superblocks, with no avail.

- Parted can see all three partitions, but has the same problem (no file system found).

I've read the Ubuntu DataRecovery Wiki and the TestDisk step-by-step guide, but nothing seems to be working.

 

Ideas?

---

### Post by roelforg on 2012-05-22
Pull the hd out of the laptop and put it in another.
Or if you have 2hd bays (most hp laptops do so i could see how yours could have one as well), put it in the second bay.

---

### Post by Don Barzini on 2012-05-22
What exactly is going on here?

You said the hard drive cable was bad. Was it replaced?..... and are you trying to retreive the data from the laptop by booting from a USB stick?

Did you move the drive to another machine?

A little more clarification as to what you are doing would be helpful.

---

### Post by roelforg on 2012-05-22
> **Don Barzini said:**
> What exactly is going on here?

You said the hard drive cable was bad. Was it replaced?..... and are you trying to retreive the data from the laptop by booting from a USB stick?

Did you move the drive to another machine?

A little more clarification as to what you are doing would be helpful.

Agreed,
When the hd cable goes bad, ofcourse there are rw errors!
Either replace the cable or put a working one in the hd.

---

