---
title: "Moving Partitions"
date: 2010-01-12
forum: General Help
---

### Post by Dylan Bartlett on 2010-01-12
Hey, My partition table is a bit screwed up at the moment. Id like to fix that. In the first partitions i have win7, the second is empty and the third has ubuntu 9.10.

I want to move the whole lot down to the left but i am unsure how. How easy is it to fix the MBR or and i being an idiot for wanting my 20 gigs back lol. Image attached to explain easier

[IMG]http://img3.imageshack.us/img3/2897/screenshot001nt.png[/IMG]

---

### Post by warfacegod on 2010-01-12
Where is sda1? This may not be a good idea but highlight sda2 select resize. In the window that comes up grab the left arrow and drag it left.

---

### Post by oldfred on 2010-01-12
If it is win7 you want to use gparted with the checkbox unchecked. If you round to partitions it will move win7 to sector 63 and cause problems. 

On second thought any movement of win7 outside of windows may cause issues. It will at the very least want to be repaired from the windows  cd/dvd. And then you will have to reinstall grub.

---

### Post by Dylan Bartlett on 2010-01-12
The SDA1 was deleted by me because it was the useless backup partition computer manufacturers have instead of boot CD's. I didnt need it anymore because i had the win 7 boot CD.

I get what you mean about moving. Its probably not worth the hassle trying to repair whats went wrong than have 25 gigs unallocated.

---

### Post by Leppie on 2010-01-12
you can add the last 5,59gigs to sda4.
reclaim the 20gigs by creating the partition sda1. like the other guys said, it's not a good idea to resize sda2.

---

