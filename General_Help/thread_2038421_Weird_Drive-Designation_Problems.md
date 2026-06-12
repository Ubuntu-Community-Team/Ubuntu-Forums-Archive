---
title: "Weird Drive-Designation Problems"
date: 2012-08-06
forum: General Help
---

### Post by Uruz on 2012-08-06
Let me first mention that I have a slew (perhaps even a plethora) of hard-drives and partitions that are all nicely organised and named and mount cleanly upon startup.

Now, a few weeks ago, I booted into my Ubuntu partition and the boot screen informed me that none of my secondary partitions or drives were mounting properly. I had had a similar problem in the past, but had fixed it with cleaning up my fstab file.

Now, I messed with stuff for a little while and eventually figured out that all of my drive designations (sda1, sdb2, sdb1, *ktp*) had been messed up (excluding my main partition's). What had once been sda was now sdb and sdc and sdd were similarly mangled. I corrected this, rebooted and everything was fine... for a few days. Then it happened again and all the drive designations had *reverted* to where they had been before. I fixed it again and it stayed fix for a few days then they changed again.

Now, I eventually figured out what was going on, but not why it was happening. I have a cell-phone (droid x) that I plug in to my computer to charge. If this phone (I believe it also works if I have a thumbdrive plugged in) is plugged in to charge (even if it's not mounted for storage) all of my drive designations are shifted while it is plugged in.

Seriously, I started up my computer today, got the mounting errors, plugged in my phone and rebooted and everything worked fine (when I figured out what was happening, everything was set up for it to work with my phone plugged in so I just do that now).

My question is this: Why is it happening and why did it start happening? Is there something I can do to fix it? I suppose it's kind of neat as a security feature (all of my storage drives are inaccessible unless a thumbdrive or phone is plugged in), but it gets annoying if I forget to plug something in when I start up.

I have not tried booting with both my phone and thumbdrive plugged in (I'm assuming drive designations would be shifted by 2 spaces)

Thanks for your help,
Uruz.

---

### Post by Cheesemill on 2012-08-06
Drives are never guaranteed to have the same designation when you boot your machine, even if you don't add or remove any devices.

This is exactly why you should designate drives using either labels or UUIDs in /etc/fstab rather than using /dev/sdXX (Ubuntu installs using UUIDs by default and has done for years).

To get the UUID of your devices do:
```
sudo blkid
```Then edit your fstab file:
```
gksudo gedit /etc/fstab
```and replace /dev/sdXX with UUID=xxx-yyy-zzz where xxx-yyy-zzz is the relevant UUID as obtained earlier.

For more information see [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

