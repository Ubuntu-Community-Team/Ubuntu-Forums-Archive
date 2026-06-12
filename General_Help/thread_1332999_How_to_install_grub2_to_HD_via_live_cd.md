---
title: "How to install grub2 to HD via live cd"
date: 2009-11-21
forum: General Help
---

### Post by keypox on 2009-11-21
I need to install grub to the partition not to mbr.  I can't find how to do this, it used to be very easy with old grub. 

Help!

BTW I tried 

$sudo mount /dev/sda1 /mnt
$sudo mount --bind /dev /mnt/dev
$sudo mount --bind /proc /mnt/proc

but none of my drives have a mnt/dev, though the root does have /mnt but its empty.  This install was working, but i installed snow leopard.  And need to add this to chameleon.

---

### Post by darco on 2009-11-21
This link should help, just scroll down...

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)



darco

---

