---
title: "&quot;Error: No Such Partition&quot; message help!"
date: 2011-01-17
forum: General Help
---

### Post by SkyGuy182 on 2011-01-17
Hi there,

   I have an Asus Eee PC 1005HAB netbook running both Windows XP and Ubuntu for netbook. I do not own a USB drive with Ubuntu on it, because a friend of mine put it on my netbook some time back. 

I've never had a problem with Ubuntu, but I've noticed that the computer was getting really slow, so I decided to restore the system. After trying to restore the system, Ghost came up, and started to restore it. But then my screen went black, and displayed:

Error: no such partition.
grub rescue>

What in the world? I've looked at different threads about this, but none of them helped. Like I said, I own an Asus Eee PC 1005HAB netbook, no CD drive, and no thumb drive with Ubuntu. 

DId I royally screw my computer? Or is there hope? 

Thank you!

---

### Post by SkyGuy182 on 2011-01-17
Bump!!! :(

---

### Post by Mark Phelps on 2011-01-18
Hard to answer your questions without additional info.

You imply that your netbook has both Windows XP and Ubuntu UNR installed. Right?

And, each is installed to its own parition(s)? Right, again?

And ... you are trying to use Ghost to restore the PC?

This is where it gets confusing.  Not owning a netbook, I have no idea what builtin tools it provides to restore itself.  So, is Ghost what is provided by ASUS? Or was it installed later by you (or someone else)?

Asking because if it IS the default, then it may look at the drive to confirm that the partitions are still intact before it does the restore -- which, when the netbook was repartitioned to add Ubuntu, are no long the case.  It then (depending on how it was configured to work), simply refuse to do the restore.

If you (or someone else) added Ghost after the fact, and you made the Ghost image after the Ubuntu install, then it SHOULD work -- but, since GRUB is installed to the MBR, it can't do the default boot it expects in order to use Ghost.

With a desktop, you might be able to get around the GRUB problem by using a bootable CD with Ghost on it -- but since your netbook probably can not boot from CD, don't know what to tell you at this point.

---

### Post by SkyGuy182 on 2011-01-24
Ghost was already on the computer, and I activated it. It loaded about halfway,went black, and I got the message. I tried booting the computer on a USB that had Ubuntu on it, but nothing happened.

---

