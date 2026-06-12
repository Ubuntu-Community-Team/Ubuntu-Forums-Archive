---
title: "How to increase the gbs of an external hard drive"
date: 2006-05-22
forum: General Help
---

### Post by tomslopez on 2006-05-22
I have an external hard drive of 300 gb, when I partitioned it the 300 gb where cut down to 279.5 to be used, but when I started copying things into the driver it said that instead of having 279.5 gb to use I had 260 gb, I had less gb to use, how can I change that to increase it without formatting the driver again?

---

### Post by Phlosten on 2006-05-23
Sounds like you may be experiencing a similar issue to a problem I have with a USB thumbdrive.
Basically Ubuntu misreports the free space available on it. When you copy stuff onto it the free space declines, but when you delete from it, it does not go the other way even though the free space is actually there.
I have not found a solution apart from using a Windows computer to copy back and forth from. I did read somewhere about turning off the USB asynchronous transfer to fix read/write buffer problems and I wondered whether this could also help this problem (although transfers would be substantially slowed). If anybody can point me to the instructions on how to do this can you let me know.

---

