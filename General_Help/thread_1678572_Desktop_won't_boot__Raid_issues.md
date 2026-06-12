---
title: "Desktop won't boot / Raid issues"
date: 2011-01-30
forum: General Help
---

### Post by omega21 on 2011-01-30
Hi there,

First off, It's been a long, long time since I've used ubuntu so I'm quite rusty on this stuff. Anyway,

I recently set up a desktop installation of Ubuntu 8.04, then upgraded it to 10.04. The system has 5 hard drives in it currently:

80  GB
1.0 TB
1.0 TB
500 GB
500 GB

The 80GB drive is where the main system / is installed. I've created a raid5 array with the other four, (the 1 TB drives are both just 500GB parts in the raid array). 

I recently copied all of my data from an external hard drive onto the raid array. I wanted to simulate a fault to test the array (as all of my data is safe on a new external drive). So, I marked one of the drives as faulty using:

mdadm /dev/md0 -f /dev/sde1

This marked one of the 500's as faulty, and Disk Utility showed my raid array's status as degraded.

I unmounted the array and hit the check/repair button, and for a quick instant I saw "repairing" with a progress bar, but then it quickly shifted to idle.

I then went to terminal and tried to assemble the array (I think this is how you repair it, right?) I ran:

mdadm -A /dev/md0

But then I got the output:

mdadm: /dev/md0 is already active- cannot assemble it.

I thought maybe rebooting might help, so I did that, and now it won't even get into GRUB.. My bios says no bootable device, which is weird because I set Ubuntu up on the 80GB drive, which is completely independent of the raid array.

So, can you help me get this booted? Thanks!! :)

---

### Post by omega21 on 2011-01-30
I just booted in with a liveCD.. For some reason my 80GB drive lost it's bootable flag.. So I used cfdisk to re-enable it.

I rebooted fine. But I'd still love to know how to further test my raid array.

Any ideas?

---

