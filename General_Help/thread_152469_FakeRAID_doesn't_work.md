---
title: "FakeRAID doesn't work?"
date: 2006-03-29
forum: General Help
---

### Post by countryboy on 2006-03-29
Hello all

I followed the FakeRAIDHowto and managed (after 3 days solid) to get it to install (there's a typo in the suggested config file for dmraid in the external link put by Sami Dalouche)

Anyway, I thought I would give it a test by disconnecting one of my SATA drives (are in a mirrored array) and bingo the box doesn't boot. Says it can't find the device /dev/mapper/isw_dhdjdkfjdkf3 (my root partition). 

So reconnected the drive and it reboots fine.

So then disconnected the other drive and bingo fails to boot again, same error message.

So my question is, what is the point of using the mirrored array as such (under uBuntu) if it doesn't automatically fall over to the other mirrored drive?

If anyone else has 2 mirrored SATA drives using FakeRAID, pull one out and let me know if it boots and why :) 

Thanks

---

### Post by exkalibur on 2006-03-29
Has the typo been fixed or reported ? I will be going through the same shortly.....

Regards

---

### Post by countryboy on 2006-03-30
Not sure, but it is on line 3, where it says PREREQ=""

If you look carefully the second " is actually a different character.

Note that it is only in the external link :

Running Ubuntu On a Fakeraid/1 array described how to adapt the original HOWTO to a FakeRAID/1 (mirroring) array

---

