---
title: "Grub error 17 &amp; unopenable harddrive"
date: 2009-09-11
forum: General Help
---

### Post by rotogenray on 2009-09-11
The power went out last night and I was away from my system, and I didn't see until I got home that, for about 15 hours my system had been overheating. I have an external capacitor-motor fan with a switch to start it, and when the power went on the motor froze and put out heat into the place where it should have been circulating air.

Long story short, the computer will not boot and comes up with grub error 17. So I try the ubuntu 8.04 alternate install as a rescue disk, and it gives me some error at the point of choosing which filesystem to use

"an error occurred while mounting the device you entered for your root file system (/dev/sda1) on target.."

So I try the normal 8.04 to just get in and poke around the hard drive. No go. Same story using Damn small. fdisk -1 gives the indication that the drive isn't being seen by the system.

Going through the installer, it can see it and the partitions- 38.5gb and 1.5gig swap, but i'd really like to rescue the data I hadn't backed up on there.

Any thoughts?


I'm running an athalon amd 64 3800+ x2
And I was running 8.04 on the old hd

And the old hd was a 40gb sata drive.

---

### Post by glenuk on 2009-09-11
Last time i got a grub 17 error i put my sata data cable in a different port on the motherboard & the error went away.
Have you tried this option yet?
Glen

---

### Post by rotogenray on 2009-09-11
Yes, that's one of the things I'd tried.

Seeing as how I hadn't moved the cables and when I left the computer it was working, I'd assume I would be able to recover without moving the cables.

Anyone else got any suggestions? What's the normal procedure for dealing with grub error 17 when fdisk won't tell you anything and you can't access the drive other than that?

I'd think maybe it thinks it's mounted weird. Is there any way to force the detection of media and/or mount it?

---

