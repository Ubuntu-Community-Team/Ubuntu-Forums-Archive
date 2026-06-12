---
title: "Ubuntu on USB"
date: 2010-08-26
forum: General Help
---

### Post by Jonny87 on 2010-08-26
I want to create a boot-able usb with Ubuntu so I can run the live cd version of ubuntu straight from a usb. no more cd's!!!

I was wondering once its made is there away that I can easily customize it? i.e add new apps (that will still be there when it next boots) etc?

---

### Post by micheledm on 2010-08-26
You can create your own personalized ubuntu iso using [http://uck.sourceforge.net/](http://uck.sourceforge.net/)

---

### Post by parker13 on 2010-08-26
> **Jonny87 said:**
> I want to create a boot-able usb with Ubuntu so I can run the live cd version of ubuntu straight from a usb. no more cd's!!!

I was wondering once its made is there away that I can easily customize it? i.e add new apps (that will still be there when it next boots) etc?

Best thing to do in my experience is to do a full install of Ubuntu onto the USB as opposed to a Live image. This has a number of advantages such as allowing full customisation including updates, just like any normal install. 

To do this, boot from CD as if you were installing Ubuntu onto your PC but select your USB disk as the installation target. The only other thing you need to do is select the advanced settings on the last page of the installation screens and tell it to install grub onto the USB disk, or it will default to the host PC's disk.

The only downside of this is that you need a 4GB stick for a full install whereas a live install will fit onto a 1GB stick.

---

