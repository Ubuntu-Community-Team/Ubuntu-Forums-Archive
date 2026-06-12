---
title: "from VM / Virutual box to HD"
date: 2009-10-22
forum: General Help
---

### Post by ethoxyethaan on 2009-10-22
Hello ubuntu's,

At school we where given ubuntu VM images, they contain software like Oracle etc, (ALL VERY EXPENSIVE STUFF THAT WE GOT FOR FREE YO!) the thing is i don't like working in the VM, id rather work on my host computer, since i'm already running gnu/linux, there is no point in me opening a VM to start using linux.

How do i get around installing this on a Hard drive, i know how to install the grubloader manually but i don't know how to make a actual "raw" image of the VM ware disk.

Help appreciated, 
Ethoxyethaan

---

### Post by P4man on 2009-10-22
Perhaps you can run a diskimager in the vm, something like partimage to make an image of the (virtual) harddrive. Then restore the image to a physical disk using SystemRescueCd or clonezilla.

---

### Post by ethoxyethaan on 2009-10-22
That was one of the possible solutions i had in mind, thanks for the input.

does anyone else have any idea's?

---

### Post by radu.ro on 2009-10-22
Maybe you can try what is suggested in [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=688872") post, only that you must try to make a live DVD from the virtual machine. How does this sound to you?

I have tried the guide for my desktop, doing an image from what I had on my laptop and it worked great.

---

