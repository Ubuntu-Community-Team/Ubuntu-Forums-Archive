---
title: "Virtualbox resizing?"
date: 2009-10-28
forum: General Help
---

### Post by phantom3113 on 2009-10-28
So here's my question: I have a Windows XP virtualmachine that I stupidly set as 8 Gigs when I made it. Needless to say, it's running out of space. Is there any way I can resize the "harddrive" of the VM without having to make a new VM? (Running VirtualBox 3.0)

---

### Post by parkland on 2009-10-28
I'm not a linux genius yet, but I THINK the following would work, unless theres an easier way:


1. Make new HD image of size you want.
2. Mount new HD image to machine as secondary HD.
3. Boot into Hirens or similar boot CD with norton ghost.(On the VM)
4. Clone your small HD to the bigger one.
5. Remove old HD, set to boot to new big HD.

This should work, please someone correct me if I'm wrong.:popcorn:

---

### Post by shaggy999 on 2009-10-29
It is possible, but only if the virtual drive image was created as a static fixed-size drive and NOT a dynamically expanding drive image. Search for a program called 'vidma'. It is very alpha stage software and could destroy the image, but it supposedly works.

The guaranteed safe way of doing it was as proposed above creating a second image drive and copying the contents using dd/ghost/clonezilla.

EDIT: Oh yeah, the methods discussed only refer to increasing the size of the virtual drive. After you do that you will then need to use a program inside the VM to resize the partitions to take advantage of the new space.

---

### Post by parkland on 2009-10-29
If you use a hirens CD image, and norton ghost, IIRC it resizes it automatically, and is relatively easy and safe.

---

### Post by phantom3113 on 2009-11-01
Ok, thanks for the help. I'll try the method(s) out once I get time :P

---

