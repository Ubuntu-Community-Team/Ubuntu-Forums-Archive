---
title: "OCZ Revodrive 3 Linux driver"
date: 2011-07-30
forum: General Help
---

### Post by keine_ahnung on 2011-07-30
Hi there,

I bought a OCZ Revodrive 3 and failed to install Ubuntu because the installer does not recognize the drive. So I searched for a driver and found -> [this]("http://www.ocztechnologyforum.com/forum/showthread.php?91847-Linux-driver-for-RevoDrive-3") (click) thread from the OCZ forums. 

It has always been a pleasure to have a fully running system out of the box without any additional drivers until now. This is the first time ever this is not the case with Linux. So, by any chance, will this change? My previous OCZ Revodrive X2 did actually work out of the box.

I know this is not a kernel-dev forum, but as I'm using Ubuntu I thought I'd ask here. Maybe you guys have an idea what to do.

Thanks,
Daniel

---

### Post by keine_ahnung on 2011-08-01
Please, anyone?

---

### Post by albatorsk on 2011-08-01
Sorry, but the RevoDrive 3 seems to be using a custom Marvell SAS controller, and while there is a driver for Marvell's controller called mvsas, it won't work without modification for the RevoDrive 3, if at all.

---

### Post by keine_ahnung on 2011-08-01
Thanks! But if I didn't get it wrong the controller should be a Sandforce SF-2281 (or two of them). Or is this something else?

---

### Post by albatorsk on 2011-08-01
I believe the SF-2281 is the NAND controller, and then just like with a regular SATA SSD you need a storage controller. Previously, OCZ fitted their RevoDrives with a SiL 3124 which has a Linux driver. That's why they work in Linux.

However, this time they used what they call "OCZ SuperScale Storage Controller" which I believe is a customised Marvell SAS controller.

---

### Post by keine_ahnung on 2011-08-01
Too bad, now I don't know if I should return the Revodrive or wait for some miracle to happen. :( I just checked some tutorial on writing linux block device drivers, but I fear this is beyond my skills. And I guess there is no open source documentation on this controller available...

But thank you for letting me know!

---

### Post by Fraoch on 2011-10-20
Wow, OCZ's lack of Linux support is very frustrating - the Revodrive is really the best SSD idea out there.

[quote=OCZ]We do not have Linux drivers for Revo3 and we are not planning any.[/quote]

[http://www.ocztechnologyforum.com/forum/showthread.php?91847-Linux-driver-for-RevoDrive-3](http://www.ocztechnologyforum.com/forum/showthread.php?91847-Linux-driver-for-RevoDrive-3)

I'll be boycotting OCZ and supporting a company that supports me.:mad:  I'll be eagerly waiting for the competition to release something like the Revo...along with Linux support.

If you look at the last post in that thread you'll see that someone did introduce a very simple patch but you must patch it into a beta kernel which you will then have to compile yourself.  I'm not sure I have the skill for that.

Vote with your wallets!

---

### Post by keine_ahnung on 2011-10-21
In fact that patch is not very complex, give it a try. Dual-Booting with Windows however does not work yet. Work in progress, without help of OCZ of course. Hooray on the Linux support of OCZ, haha!

---

### Post by Fraoch on 2011-10-21
> **keine_ahnung said:**
> In fact that patch is not very complex, give it a try.

I have compiled a kernel in Gentoo but I've never applied a patch.  Compiling is straightforward in Gentoo, I've never tried it in Ubuntu.  I guess if you know how to compile a kernel, applying a patch is easy.

The patch does look very simple - it simply seems to identify the drive using hex strings.

> Work in progress, without help of OCZ of course. Hooray on the Linux support of OCZ, haha!

It's just really upsetting because the price of the small Revodrive has come down a lot - in fact right now it's on sale for a little more than a SATA3 Crucial M4 SSD of about half the capacity!

While the M4 is one blazing fast SSD, the Revo will simply blow it out of the water in terms of speed.  It makes me upset that this product is so superior yet OCZ, a company supposedly for computer enthusiasts and power users, refuses to support Linux, a community of computer enthusiasts and power users!  It does not give me a good feeling about them or their products which means I wouldn't enjoy using a Revo as much as I should...

---

### Post by bloke2400 on 2011-12-13
I was reading this today. Hopefully it is of some use to you.

[http://www.ocztechnologyforum.com/forum/showthread.php?95151-Linux-patch-support-for-RevoDrive3-RevoDrive3-X2-zDrive-R4]("http://www.ocztechnologyforum.com/forum/showthread.php?95151-Linux-patch-support-for-RevoDrive3-RevoDrive3-X2-zDrive-R4")

---

### Post by dargaud on 2011-12-13
Before commiting all your data ot OCZ, maybe you need to [read this information]("http://hardware.slashdot.org/comments.pl?sid=2550708&cid=38211850")... I know I have an OCZ in one of my systems, and now I'm scared

---

