---
title: "Usb gone!!??"
date: 2010-11-26
forum: General Help
---

### Post by Jamezo97 on 2010-11-26
Hi,
I have recently been trying to get a version of windows XP onto my USB(so i can run itunes etc.)
I changed the bios so it thought that my USB was a hard drive, then I inserted my Windows XP disk.
If came up to the first stage, with all my different partitions. I told it to delete my USB partition and to then format it.
It deleted it, but could format it.
I then ran restarted my computer changed the bios so it would boot from my hard drive. Then once Ubuntu had loaded I inserted my usb.
And now ubuntu can't find any trace of my usb. I can't do anything. I ran windows xp inside virtual box(VERY slow) and it couldn't find my USB either!
My usb ciost a fair bit, and has four gig on it, and I dobn't want to throw it out.
Anyone who knows how to fix this? Any help would be GREATLY APPRECIATED!!
Thanks!

---

### Post by dino99 on 2010-11-26
open synaptic and check that:

mountall & usbmount are installed

sudo apt-get install -f
sudo dpkg --configure -a

---

