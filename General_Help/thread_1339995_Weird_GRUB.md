---
title: "Weird GRUB"
date: 2009-11-28
forum: General Help
---

### Post by jensen1604 on 2009-11-28
Hi guys.
Just noticed a couple of days ago that my GRUB has changed a bit, though I haven't had any time think about it until now.

Thing is, I'm dual-booting Ubuntu 9.10 with Win XP SP3, but my GRUB has changed in someway, why I don't know? :p

As default I'm pretty sure it looked something like this:

Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Microsoft Windows XP (on /dev/sda4)

but now it looks like this:

Ubuntu, Linux 2.6.31-15-generic
Ubuntu, Linux 2.6.31-15-generic (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Microsoft Windows XP (on /dev/sda4) 

Any help is greatly appreciated!!
jensen1604

BTW: my grub is GNU GRUB version 1.97 beta4

:popcorn:

---

### Post by maduranga on 2009-11-28
I also have the same thing. this is happening cos of kernal upgrades ?

you can edit the grub menu by yourself. 

> gksudo gedit /boot/grub/menu.lst

but be careful when doing that, wrong settings could prevent from booting into either of your OSes

(thats what i did to remove duplicate entries.. some one please correct me if im doing it wrong! )

---

### Post by Elfy on 2009-11-28
Yes - there was a kernel upgrade a few days ago.

---

### Post by jensen1604 on 2009-11-28
Oh :O I see ..
Is there anyway to resolve this, and what happens if we boot into the old kernel?

I don't think I have that "menu.lst" file.. Can't seem to find it anywhere in the grub folder, and when I run the command 
gksudo gedit /boot/grub/menu.lst, it just opens a new blank text document and when I close it, it asks if I wanna save the docuement? :O

---

### Post by Elfy on 2009-11-28
> **jensen1604 said:**
> Oh :O I see ..
Is there anyway to resolve this, and what happens if we boot into the old kernel?

Not sure what you mean by resolving this?

I like to keep the current and previous kernels - at least until I am sure nothing untoward is happening.

You can remove the old kernel in synaptic if you wish and then after grub has updated you'll only be left with the new one.

If you boot with the old kernel then you would be booting without any changes made to the new one - at least that is my understanding.

---

### Post by jensen1604 on 2009-11-28
> **forestpiskie said:**
> Not sure what you mean by resolving this?

I like to keep the current and previous kernels - at least until I am sure nothing untoward is happening.

You can remove the old kernel in synaptic if you wish and then after grub has updated you'll only be left with the new one.

If you boot with the old kernel then you would be booting without any changes made to the new one - at least that is my understanding.

I see, so better just leave it for now then? :) I was just curious about what had happened and now I know. Since it ain't hurting anyone or anything, I'll just leave it there for now :)

Thanks for all the help guys :popcorn:

---

