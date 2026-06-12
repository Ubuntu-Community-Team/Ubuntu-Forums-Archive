---
title: "Migrating Ubuntu to different drive"
date: 2010-09-23
forum: General Help
---

### Post by Objekt on 2010-09-23
My Ubuntu 9.10 install is on a positively ancient Hitachi Deskstar SATA hard drive.  While there are no screaming red flags in its SMART monitoring info - yet - the drive is around 7 years old, and probably due to expire any day.  I have already had a couple of other HDDs die at younger ages.

So, it's probably time to move my Ubuntu install to a newer hard drive on this machine.  Is it not a big deal to move an existing Ubuntu install to a different hard drive, or is that just not going to work?  What bits might react poorly to being moved to a different drive, and what, if anything, will I need to fix manually?

I'd prefer to have some idea what's going to happen before I go to all the trouble of juggling partitions, imaging, etc.

---

### Post by bodhi.zazen on 2010-09-23
IMO it is almost as easy to install Ubuntu. Personally I advise you keep a separate /home or /data partition so you may install an os and preserve your data.

To move your partition, IMO, it is easiest to use gparted, from a live CD. gparted will copy and past the partition.

After that, from the live CD, re-install grub to the new HD and edit /etc/fstab on your unbuntu root partition to update the uuid of the root partition.

---

### Post by Objekt on 2010-09-23
Sounds straightforward enough.  I have been keeping /home on its own partition since ...well, ever since I started using Linux, for the reason you stated.

Gparted does sound like the easiest way to do this.  The more complicated part will be making room on the newer hard drive.  Must juggle/resize some partitions.

---

