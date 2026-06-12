---
title: "Unable to mount cdrom0"
date: 2010-05-10
forum: General Help
---

### Post by Khorre on 2010-05-10
Alright, I've got an annoying issue.
Won't let me mount my CD drive. I had this issue once before and I solved it, but I don't remember how. All I remember was that it was frustrating.
Searching around I see many others with the same problem, yet no good answer (or answers that I can get to work for me)

The problem is this: when I place a CD in the tray and close it, nothing happens.
When I try to manually mount it, I get an error message:

mount: special device /dev/scd0 does not exist

Funny, because i'm pretty sure /dev/scd0 existed just yesterday when I used it last.
So without finding out how I fixed it last time, i've decided to go ahead and just ask myself, can anyone help?

(I am using Mint, based off of Karmic Koala I think)

---

### Post by Khorre on 2010-05-10
-=bump=-

---

### Post by Khorre on 2010-05-10
-=bump=-

---

### Post by Khorre on 2010-05-10
-=bump=-

---

### Post by Khorre on 2010-05-11
-=bump=-

---

### Post by royleith on 2010-05-14
Yes, I have the same problem and have done through various versions of Kubuntu and Ubuntu on three computers. The fix is easy, but irritating. Leave a CD or DVD of the type with which you want to work (e.g. R, RW or non-writable) and reboot Linux. new CDs or DVDs should then be detected. There is still the issue that a CD-R might be detected, but that a CD-RW will not, requiring a reboot.

It seems that the hal-daemon does not detect some device types unless the device is already loaded with the appropriate media during boot-up. i am searching the forums to see if there is a fix that does not require a reboot.

Regards
Roy Leith

---

