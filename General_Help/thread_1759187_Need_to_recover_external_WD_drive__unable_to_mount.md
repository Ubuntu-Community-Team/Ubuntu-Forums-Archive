---
title: "Need to recover external WD drive / unable to mount."
date: 2011-05-15
forum: General Help
---

### Post by whvann08 on 2011-05-15
Hello I am trying to recover data on an WD external hard drive. 1tb.  Not able to mount this drive in window or on linux.  Is there a way to force a mount on this drive.  The drive spins up but I cannot access it .  I have tried with Win XP and Ubuntu 11.04.  Any help will be great.

Henry

---

### Post by Hedgehog1 on 2011-05-15
From Ubuntu, please use the Disk Utility to look at this external hard drive, and then check it's SMART health status.

Please post the SMART status if you are able to talk to the drive at all.

Depending on it's current level of failure, you may be able to use ddresuce to copy the data on the disk to a new disk of the same size or greater size.


***The Hedge***

:KS

---

### Post by whvann08 on 2011-05-15
I checked it with the disk utility program and did not get a smart status from this drive.  I don't know what extent the failure is but I have not been able to access it in any way.  Like I said this is a WD My book 1tb drive.  I have changed usb cables just to make sure that was not it.


Henry

---

### Post by Hedgehog1 on 2011-05-15
Sadly, this is not looking good.

If the drive is spinning up (and not making the loud 'WD clicking of death' sound), you may be seeing a failure of the USB to SATA board in the external case.

If you take the case apart and install the hard drive in a system with a spare SATA port, you might find the drive is fine.

I will be honest and warn you that a drive failure is more likely than the USB to SATA failure, but it is a possibility worth exploring.


***The Hedge***

:KS

---

