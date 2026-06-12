---
title: "USB Flash Drive Rescue"
date: 2011-10-30
forum: General Help
---

### Post by LordAro on 2011-10-30
Hi,

It seems that flash drive has broken

It is a Corsair Flash Voyager 16GB (USB3)

Upon trying to mount it displays: "Error mounting: mount: /dev/sdb1: can't read superblock"

and "sudo fsck /dev/sdb1" displays:
"There are differences between boot sector and its backup"

when selecting either of the 3 options, it displays:
"Both FATs appear to be corrupt. Giving up."

I can probably accept that my flash drive is broken, but is there a way to rescue my files?

---

### Post by dcstar on 2011-10-31
> **LordAro said:**
> Hi,

It seems that flash drive has broken

It is a Corsair Flash Voyager 16GB (USB3)

Upon trying to mount it displays: "Error mounting: mount: /dev/sdb1: can't read superblock"

and "sudo fsck /dev/sdb1" displays:
"There are differences between boot sector and its backup"

when selecting either of the 3 options, it displays:
"Both FATs appear to be corrupt. Giving up."

I can probably accept that my flash drive is broken, but is there a way to rescue my files?

Use **ddrescue** to copy as many blocks as possible from the drive to a file, then mount the file using the "loop" option and use **testdisk** to try and scan it for a recoverable partition.

You can probably download disk recovery CDs that basically do the same thing.

---

### Post by LordAro on 2011-10-31
hi, 

thanks for your suggestions, i'll  try them asap, but 1 question:
> ...then mount the file using the "loop" option ...
how would i do this? is there a guide anywhere?

---

### Post by LordAro on 2011-11-01
Fixed! :D

FYI, i used testdisk to find and copy my files from my broken flash drive,

after managing to get around some corrupted files (some sort of recursive folders), i attempted to re-format the disk.

i didn't (initially) know how to do it with linux, so i used a vista box, which failed to reformat it, freezing after the progress bar showing about 9/10 completed. that failed in exactly the same way, several times
then tried gparted, which also failed, but after attempting to reformat on a windoze 7 laptop (which still failed, just not so badly) i tried gparted again, which worked! :)

the (re-)transfer is currently in progress...

EDIT: now, how do i mark thread as solved?
EDIT2: found it! :)

---

### Post by Myjab on 2012-05-06
Can you plz tell me the commands to do it. Since i don't commands in linux to use

---

### Post by ericpeac0ck79 on 2012-06-23
> **dcstar said:**
> Use **ddrescue** to copy as many blocks as possible from the drive to a file, then mount the file using the "loop" option and use **testdisk** to try and scan it for a recoverable partition.

You can probably download disk recovery CDs that basically do the same thing.

thanx 4 this.

here's what i did:
i was copying music to my phone.
i clicked safely remove device in the windows system tray, but i forgot to click turn off usb storage on my phone.
i pulled the usb cable, and my android 2.3 phone said "damaged sd card"
i was like wth!
i put the sd card in my computer, and it froze up windows explorer and disk management
next, i powered up my ubuntu virtual machine. i found that the partition was still there, but damaged. (can't read superblock)
after some googling, i found this thread.

i created a new virtual disk and attached it to my ubuntu VM
next, i ran ddrescue and copied the damaged sd card to the new vitrual disk

after that, i ran testdisk.
it took a few tries, and playing with different menu choices, but i was able to get my files back using test disk.
after they were copied to a new folder, i playred with testdisk some more - rebuilding the boot sector did the trick. after that i was able to mount the partition normally and copy files.

copying the files to a new sd card now. 

now, here's something weird:
the original sd card i was using (16GB) would lock up windows explorer and disk management, so i couldn't do anything with it in windows (duh)
but even in ubuntu, i was unable to successfully create a new partition and format it (fat). it would either give me an error, or appear to work, but then nothing would be changed.

finally, i just deleted the entire partition and stuck the sd card back in my phone.... ANDROID was able to successfully repartition and format the sd card....
*_why would android be able to get the job done when both windows and ubuntu couldnt?_*

---

### Post by GreatDanton on 2012-06-23
Interesting thread. Is your sd card working like before or not? Is corrupted or not?

---

### Post by ericpeac0ck79 on 2012-06-23
> **GreatDanton said:**
> Interesting thread. Is your sd card working like before or not? Is corrupted or not?

it seems to work ok now.
i just copied a bunch of stuff to it and put it in my android tablet... no probs so far.

again, i find it weird that android could partition and format it properly when windows 7 and ubuntu couldn't....

---

### Post by ericpeac0ck79 on 2012-07-11
two weeks later, and no probs with sd card.

btw, the ddrescue image restore went off without a hitch.

---

