---
title: "UUID Changed, Difficulties during Boot."
date: 2012-03-03
forum: General Help
---

### Post by Aurauxis on 2012-03-03
So I had Ubuntu 11.10 on an portable mini-usb external hard drive and I was enjoying it thoroughly until one day, the usb port had broken off. I purchased an inexpensive portable hard drive enclosure, and put the old drive into that. Then, I plugged it in to my computer and Ubuntu would not boot. I tried the Recovery mode from the Grub menu and after a string of lengthy boot messages, I came across an error, followed by initramfs prompt/BusyBox. I am almost certain this is due to change in UUID. How can I edit fstab through initramfs to have it fixed to the new adjustment (and find my new UUID, for that matter)? For whatever reason, my version of BusyBox has no text editor, not even vi.
Any help is greatly appreciated!

---

### Post by raja.genupula on 2012-03-03
Hi please try this 
[http://ubuntuforums.org/showthread.php?p=11735008](http://ubuntuforums.org/showthread.php?p=11735008)

---

### Post by Aurauxis on 2012-03-04
Thank you. Reading through those posts had brought me an idea, and I was able to locate my fstab.
The UUID is correct... #-o
Well, I guess I could try the instructions that were provided. I'll be back in a bit.

---

### Post by Aurauxis on 2012-03-04
Nope, no success.

---

### Post by raja.genupula on 2012-03-04
any progress ? have you tried all the methods in it ?

---

### Post by Aurauxis on 2012-03-04
Just found out, I can boot through (just one) older kernel version.
But no internet, and I am having graphical difficulties.

---

### Post by Aurauxis on 2012-03-04
And yes, I have.

---

### Post by raja.genupula on 2012-03-04
No internet means , what about it please explain . 
while coming to your graphics please reinstall the drivers .

---

### Post by oldfred on 2012-03-04
Is enclosure separately powered? 

Some have reported issues with underpowered external drive running from USB only. And/or drives being slow to mount and causing problems.

---

