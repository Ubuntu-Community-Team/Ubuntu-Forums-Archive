---
title: "Can't enable desktop effects after removing old driver"
date: 2010-08-28
forum: General Help
---

### Post by oleink on 2010-08-28
I've got an ati x1270 in my laptop and removed the fglxr driver and now I can't enable desktop effects and the preinstalled driver clearly isn't working and I don't really want to reinstall ubuntu AGAIN.  I'm getting tired of it.  I wouldn't have removed the driver except that I think it was effecting my booting because I was booting to a blank screen (and it wasn't my ram)

---

### Post by Frogs Hair on 2010-08-28
I think you will need the proprietary drivers to enable  3D applications. I use Nvidia , but the hardware   drivers jockey informs me that I need the proprietary driver to enable desktop effects.

---

### Post by oleink on 2010-08-28
> **Frogs Hair said:**
> I think you will need the proprietary drivers to enable  3D applications. I use Nvidia , but the hardware   drivers jockey informs me that I need the proprietary driver to enable desktop effects.

That's the problem it was preinstalled before and I actually have every ati driver installed now and it isn't working

---

### Post by kelvinho on 2010-08-28
Hey there.

To enable desktop effects, you need the proprietary drivers.

I have an Nvidia card that doesn't get on very well with the Linux driver, and crashes frequently, giving nothing but a blank screen on boot up. I have had to learn to do without it; the x-org drivers are all I have.

It's a shame. I do not get the same problem with Leopard or Windows, just Linux :KS

Sorry to let you down the hard way. (Have you tried to see what is happening in x-org.conf?)

Still using Linux! Ubuntu, Debian, Gentoo and when desperate, Suse!

---

### Post by oleink on 2010-08-28
> **kelvinho said:**
> Hey there.

To enable desktop effects, you need the proprietary drivers.

I have an Nvidia card that doesn't get on very well with the Linux driver, and crashes frequently, giving nothing but a blank screen on boot up. I have had to learn to do without it; the x-org drivers are all I have.

It's a shame. I do not get the same problem with Leopard or Windows, just Linux :KS

Sorry to let you down the hard way. (Have you tried to see what is happening in x-org.conf?)

Still using Linux! Ubuntu, Debian, Gentoo and when desperate, Suse!

Hey thanks.  I must not have said something right because the prebuilt proprietary driver for my card allowed me to use compiz before I installed the other driver but on removal of the other I couldn't get the original to work.  I did in fact just reinstall and now I have compiz again so I guess this is solved but only the long way

---

