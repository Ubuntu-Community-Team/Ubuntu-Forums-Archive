---
title: "Resizing partition"
date: 2011-05-20
forum: General Help
---

### Post by ki4jgt on 2011-05-20
Have a linux system (RootNexus' Userland interface, Zipit Z2) I know this isn't the primary place for this OS, but hypothetically (Not holding anyone responsible for my actions except me) if a dd image exists for a 1gb SD card and I make a 1gb partition on a 4 gb card, (The 1gb partition has an EXT3 and SWAP) can I stretch the EXT3 to fill the extra space in the card without affecting boot?

---

### Post by Hedgehog1 on 2011-05-20
I did this successfully with a hard drives.

I did ddrescue (had some bad sectors so I could not use dd) & copied 640gig hard drive to 1tb hard dive, and then expanded the partition to the full size of the 1tb hard drive.

It should be fine!

***The Hedge***

:KS

---

### Post by jerrrys on 2011-05-20
you could also have a look at [clonezilla]("http://clonezilla.org/")

---

### Post by ki4jgt on 2011-05-20
[http://zipit.rootnexus.org/files/Z2-USERLAND/RC1-PRE2/](http://zipit.rootnexus.org/files/Z2-USERLAND/RC1-PRE2/) OK, I followed these instructions to the T. I was able to mount the image just fine, but when it came time to copy it onto the microSD. The machine stared to copy and showed a ton of files it was copying. Then all of the sudden it stops on busy box and says it's out of room. The image is 1gb big and the flash drive is 4. I partitioned the flash drive with .5 gb SWAP and 3.5 GB of EXT3. Anyone know what's going on?

EDIT: All that is on the SD is lost and found.

---

