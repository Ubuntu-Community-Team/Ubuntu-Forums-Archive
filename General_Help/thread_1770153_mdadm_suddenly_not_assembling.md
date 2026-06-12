---
title: "mdadm suddenly not assembling"
date: 2011-05-28
forum: General Help
---

### Post by bobbob1016 on 2011-05-28
I have a computer running 10.10 as a simple fileserver, with an mdadm softraid5.  It was working fine (I had to assemble the raid by hand after each reboot).  Now it won't assemble, it keeps saying "two devices isn't enough to start the array" or "device or resource busy" (referring to one or more drive).  I can see the drives with gparted, but still can't assemble the array.  I'd appreciate any help on this matter.

I ran "sudo mdadm --assemble --verbose /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde /dev/sdf1" and got this: [http://pastebin.com/TcrSr7k3](http://pastebin.com/TcrSr7k3)
*I know I'm using /dev/sde not /dev/sde1, I added the whole drive, not the first partition, I'd fix it, but it was working, and I don't want to play with it when I don't have it all working to begin with.

---

### Post by bobbob1016 on 2011-05-28
I got is solved.  When I did "sudo mdadm -E /dev/(each of the drives in the array)" I noticed that the superblocks said different things, but had the same "magic number".  I did "sudo mdadm --assemble --force /dev/(array) /dev/(each drive)" and I got 4 out of the 5 to come back.  It's a raid5, so I just added the 5th one back, and it's rebuilding.  My data is still there though.

---

