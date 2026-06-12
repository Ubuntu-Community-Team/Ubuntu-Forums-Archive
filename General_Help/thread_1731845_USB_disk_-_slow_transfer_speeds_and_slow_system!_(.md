---
title: "USB disk - slow transfer speeds and slow system! (meerkat)"
date: 2011-04-17
forum: General Help
---

### Post by benplanet on 2011-04-17
Whenever I transfer a movie into my 16GB USB flash disk, my whole system becomes windows-like and unusable! 

When i drag the file(s) into the USB disk folder, it starts out fine and pretty darn fast (25mb/sec) then slowly decreases until it's unbearably slow (3m/sec) and as a side effect my whole system starts deteriorating. I basically have to wait for the file to finish transferring before i can use my desktop again!

This has been happening with every version since Karmic (all 64bit)- I put up with it because I don't use the USB stick that much.. but lately it's been my go to source for transfering large files to/from work.

Anyone run across this problem? anything I can do to appease it or completely solve it? 

Thanks!

---

### Post by benplanet on 2011-04-22
bump... anything i can do? save trying to upgrade to natty?

---

### Post by KegHead on 2011-04-22
Hi!

Curious about your ram.

Please post result of:

"top"

KegHead

---

### Post by vallero on 2011-04-28
It should be just a matter of disabling USB Legacy Support and enabling AHCI within BIOS.
That should speed up everything, at least for me.
Tried on Lucid 64.
Cheers

---

