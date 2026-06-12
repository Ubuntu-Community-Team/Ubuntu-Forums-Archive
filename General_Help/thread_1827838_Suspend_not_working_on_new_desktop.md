---
title: "Suspend not working on new desktop"
date: 2011-08-18
forum: General Help
---

### Post by Kallun on 2011-08-18
Well hello there :)

I just built my new desktop yesterday, I got elementary Jupiter (built on Ubuntu 10.10) installed and running fine on it, everything works... except for when I tell it to suspend :(

Upon selecting suspend, the monitor goes black for all of about a second and then comes straight back to the lock screen, pretty damn irritating.

I'm running a 64 bit system on kernel 2.6.35-30.

Not sure if I need to provide any further info.

Any help is greatly appreciated, thanks in advance :D

---

### Post by dino99 on 2011-08-18
you need at least a 4 Gib swap partition for suspend/hibernation.

---

### Post by Kallun on 2011-08-18
Thanks for the swift reply dino :)

Ah, that's probably where the issue lies then! I have a 2.33GB swap partition.

Okay... one question though, I've played with changing sizes of partitions on an installed system before, using gparted live... and it did not go well, it rendered my Linux system unbootable :(

How can I go about enlarging my swap partition without causing any issues?

---

### Post by CrusaderAD on 2011-08-18
You're playing with fire there, man. Changing partitions is tricky. I did some looking around and it seems like these guys had a few ideas: [http://www.linuxquestions.org/questions/linux-newbie-8/how-to-increase-swap-partition-space-92924/]("http://www.linuxquestions.org/questions/linux-newbie-8/how-to-increase-swap-partition-space-92924/")

---

### Post by pqwoerituytrueiwoq on 2011-08-18
Swap is not required for suspend it is for hibernate and the required swap spaced depends on your ram

---

