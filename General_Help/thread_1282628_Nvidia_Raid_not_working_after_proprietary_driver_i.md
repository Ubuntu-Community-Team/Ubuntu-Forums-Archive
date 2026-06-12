---
title: "Nvidia Raid not working after proprietary driver install"
date: 2009-10-04
forum: General Help
---

### Post by CommanderKeen on 2009-10-04
Unfortunately I'm relatively unfamiliar with linux, and thus chose Ubuntu.  I have just recently installed Ubuntu 9.04 x64 with gnome on my pc (Gigabyte ga-m57sli-s4) with nVidia nForce 570-SLI chipset, which has RAID functionality, but from what I've read is what's considered fakeRAID. I have a SATA mirrored RAID array but it is seen as 2 seperate drives in ubuntu.  I am dual booting windows XP and ubuntu, so I know my array is still intact through windows, but for some reason, ubuntu wants to treat it like 2 drives.  I tried installing dmraid, through synaptic package manager, but then both drives disappeared altogether.  

Please forgive my ignorance.  I'm sure this is a simple problem, and will be very grateful for any help I can get.

---

### Post by CommanderKeen on 2009-10-04
Ok, so continuing, I guess there was never really a problem?  
I've tried the dmraid -ay thing, which seems rather pointless, as I can manually mount a device /dev/mapper/nvidia_jhafigbb1 to a /media/SATA Backup that I created, and browse nicely in nautilus (haven't tried writing to it yet).

I have another device nvidia_jhafigbb which is "busy" if I try to mount it.  

looking at my drives in gparted, I see 4 entries that all appear to be my SATA RAID drive(s).  Two are identical; showing the partitions, AND the unallocated space--they're called sda and sdb.  One is the /dev/mapper/nvidia_jhafigbb, and it shows the same, and another is /dev/mapper/nvidia_jhafigbb1 showing only the partitioned space on this drive.  

I'm worried about writing to the array incorrectly, and destroying my data, and I also want the array to show up in nautilus, just like my IDE drives--my windows partition, etc. which are visible and easily mountable.

I apologize in advance for my ignorance; I'm a first-time linux user, and I've been all over the internet, but nothing seems to apply, or want to give me a solution that makes the interface intuitive.  Hope someone out there can shed some light on the situation, because I have nearly gone bald fighting with this!

---

### Post by psusi on 2009-10-07
You want to ignore sda and sdb, as those are the individual disks that make up the array and you don't want to touch those.  /dev/mapper/nvidia_jhafigbb is the raid array, which appears to contain only one partition ( nvidia_jhafigbb1 ) and THAT is what you want to mount to access your windows files.  By the way, when you installed Ubuntu, where did you install it?  Or are you just using the livecd?

---

