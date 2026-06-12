---
title: "copying to usb why 100% for so long?"
date: 2012-06-08
forum: General Help
---

### Post by ELD on 2012-06-08
Does anyone else get it where a file will copy over to a usb drive and then just sit there when it says all of it is done?

---

### Post by VMC on 2012-06-08
I get that when I copy a large file, because the buffer hasn't been flushed yet. Have you notice any activity on the usb (lights flashing)?

---

### Post by fcorourke on 2012-06-08
Hi :-) -- I just installed 12.04 & copied some needed file [about 128 gigs] it took fore ever transfering to a USB 3 drive with a USB 3 cable &  2 USB 3 ports, like 4 megs a second tops & slowed down. Not sure if or what, but not what I expected. Does 12.04 not SEE USB 3 ??? Took ages & said finished & it was not -- when I stopped still trying to do copy in background after I dismounted.... Is this a problem or a fluke????

    Fred  :confused:

---

### Post by ELD on 2012-06-09
> **VMC said:**
> I get that when I copy a large file, because the buffer hasn't been flushed yet. Have you notice any activity on the usb (lights flashing)?

Yeah the lights still flash was only 1.8gb not exactly massive either.

 Is it a bug?

---

### Post by philinux on 2012-06-09
> **ELD said:**
> Yeah the lights still flash was only 1.8gb not exactly massive either.

 Is it a bug?

Long standing bug. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500069](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500069)

---

### Post by ELD on 2012-06-09
> **philinux said:**
> Long standing bug. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500069](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/500069)

Does it only affect windows based file systems? If i put my stick to say ext3 would it still happen?

---

### Post by philinux on 2012-06-09
> **ELD said:**
> Does it only affect windows based file systems? If i put my stick to say ext3 would it still happen?

Seems to affect all file systems. Large copies only. I've never seen a freeze only a gradual slowdown in xfer rate.

This only happens copying from HDD to external usb stick for me.

---

### Post by ELD on 2012-06-12
Odd it doesn't happen everytime, i was able to try it another day and it completed in 5 minutes.

---

