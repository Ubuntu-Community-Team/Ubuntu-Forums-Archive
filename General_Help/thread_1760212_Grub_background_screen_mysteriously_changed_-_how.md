---
title: "Grub background screen mysteriously changed - how?"
date: 2011-05-16
forum: General Help
---

### Post by james_mcl on 2011-05-16
I've installed 64-bit Ubuntu Natty on two separate laptops. On one of them, I did an upgrade install from Maverick; and when Grub appears to offer me a choice between Natty and Hardy, it has a plain black background.

On my other laptop, I installed Natty from scratch (booted from the live CD as soon as I got the machine out of the box.) I'm pretty sure that Grub had the same plain black background on the first occasion I booted up after this, (the choices now, however, being Natty or Win 7 - shudder!).

But on subsequent boots, the Grub screen has had a background with a little cartoony picture of the planet Earth at the bottom, a reference to Debian, some stars and a rocket with a spiralling trail behind it... It looks *very* nice indeed, but I didn't make any changes to Grub's configuration and I'm at a loss to know what caused the change or why the difference between the two laptops!

I did install Gnome in Ubuntu Software Center under the (possibly mistaken) belief that no version of Gnome was currently installed to run Ubuntu Classic with; could this be related?

Does anyone have any idea how this happened?

Thanks,

James McLaughlin.

---

### Post by Hedgehog1 on 2011-05-17
The newer version of grub2 installed with Natty will incorporate a picture in the menu if it finds a picture in the /boot/grub directory.

If you look in that directory, I am expecting you will find the picture in the directory (possibly from an earlier attempt at making the grub menu look fancy).

***The Hedge***

:KS

---

### Post by james_mcl on 2011-05-18
Intriguing... I have no idea how it got set to this, but the image turned out to be

/usr/share/images/desktop-base/spacefun-grub.png

I think I'm going to have a look through there later tonight, and find out how to set the image myself.

Thanks!

---

### Post by TimHeckman on 2011-06-13
> **james_mcl said:**
> Intriguing... I have no idea how it got set to this, but the image turned out to be

/usr/share/images/desktop-base/spacefun-grub.png

I think I'm going to have a look through there later tonight, and find out how to set the image myself.

Thanks!

I noticed the same thing.  It appears that somehow the Debian Squeeze grub configuration made it in to the Natty repositories?  I'm not quite sure.

I wonder if the package maintainers messed up.

---

