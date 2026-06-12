---
title: "USB pen drive problem... sort of."
date: 2012-09-03
forum: General Help
---

### Post by Dy1anW on 2012-09-03
Not long ago, my girlfriend copied files to a USB stick (we'll call this stick #1), but absentmindedly pulled it while it was being written to (this is on her computer, btw, using ubuntu 11.10). Naturally I plugged it back in to check the damage and found the drive was stuck in read only mode. The first remedy I tried was a reboot; that didn't change anything. I tried to see if I could change it back to read/write under properties. That didn't work. I tried fscking it; nothing. Since it's a FAT32 partition, I tried dosfsck as well, and when that didn't help I resorted to gparted to repartition and format, and it couldn't do that either. At this point I thought maybe the stick was buggered, so I tried another one (stick #2) and that was stuck in read only as well (and nothing traumatic had occurred to that stick). I figured maybe the USB port was locked in a write state (despite the reboot), but according to *fuser*, there was nothing accessing the port. I decided to kill all processes to that port regardless and reboot; still nothing.

Enter stick #3 (this one's mine). For some reason, my device was read/writable, yet sticks #1 & #2 were still read only after swapping them out. That to me is just weird. Any clues?

Also should point out that none of the above mentioned sticks have a physical write protect switch.

---

### Post by Grenage on 2012-09-03
Have you tried repartitioning and formatting them?  Start with a blank slate, so to speak.

---

### Post by Buntu Bunny on 2012-09-03
This is no help but I had the same problem with my usb stick after copying files from a library computer (Windows). When I got home and tried to copy the files on to my computer (then Ubuntu 10.04) the permissions had been changed to read only. The best advice I could get from the forum was to reformat. I hope you find a better solution.

---

### Post by Dy1anW on 2012-09-04
I already tried that: "and when that didn't help I resorted to gparted to repartition and format, and it couldn't do that either."

---

### Post by Grenage on 2012-09-04
If you boot from a live CD, can you write to the USB drives?

---

### Post by Dy1anW on 2012-09-04
> **Grenage said:**
> If you boot from a live CD, can you write to the USB drives?
I'll have to give that a try tomorrow when I'll next have access to her computer. Come to think of it, it would have been good practice to have left a Live CD at her place for situations just like this. It's not like having a spare copy there would break the bank :p

---

### Post by Dy1anW on 2012-09-05
Posting a new reply so you'll see this.

Okay, so I booted from Live CD, tried copying files over to sticks #1 and #2, and had the problem that they were read only. Additionally, I also tried copying files to a brand spanking new stick (#4) and it was also stuck in read only. Surely booting from Live CD should have negated any locks put in place? :confused:

---

### Post by t0p on 2012-09-05
In the past I have experienced this (usb sticks becoming read-only) and the only solution was to replace them.  The shops never really questioned it, they'd just mount the stick to check it wasn't something simple, then replaced the sticks readily.  I think it may be a problem with sticks in general, especially the cheap ones.  But your experience seems to be out of the ordinary.

I suggest you check the usb interfaces thoroughly, with other sticks and other devices.  Your experience makes me think "hardware problem"... and if it isn't the sticks, it may be your computer.  But then you did say this happened on more than one computer...

I dunno.  Check check and check again, multiple usb devices and multiple computers.

---

### Post by Grenage on 2012-09-06
> **Dy1anW said:**
> Surely booting from Live CD should have negated any locks put in place? :confused:

Yes, if the problem was software.
No, if the problem was the USB drives or the hardware.

You tried a new stick; do any or all of the sticks work in an alternative PC?

---

### Post by Dy1anW on 2012-09-08
Alright, so I've now tested all sticks on two computers. Here are the results:

Stick #1 (this is the one that was pulled while being written to) - read only on both computers. I think we can safely say that this stick is f... dead.

Stick #2 - previously this was stuck in read only on my girlfriend's computer (Comp #1), but quite bizarrely this is now writable - so no complaints there.

Stick #3 - This is one of mine, and was always read/writable on both computers.

Stick #4 - This is the new one, and was read only on Comp #1, but like Stick #2, has suddenly and inexplicably become read/writable.

I'll go ahead and mark this thread solved, even though the mechanism behind the change in behaviour of sticks #2 and #4 are still a mystery.

---

