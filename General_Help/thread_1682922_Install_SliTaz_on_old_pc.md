---
title: "Install SliTaz on old pc"
date: 2011-02-06
forum: General Help
---

### Post by 4042966262 on 2011-02-06
trying to restore and old pc(its an old gateway.), impressed with Slitaz and want it as main and only OS. burning .iso to CD and loading it loads boot screen, then blinks to a (DOS?) screen showing bits of code. i was told this means that it ran out of ram? and or space to install. i am trying to boot Siltaz from floppy now, how can i burn Slitaz to a floppy? the pc i am posting this question on is running Lubuntu and has a floppy drive.

---

### Post by topher-t-mill on 2011-02-06
I did have slitaz running on 128 mb of ram, but I have tried installing it to a 256mb usb with no success, Could it be some grease or a scratch on the cd?

---

### Post by marshag63 on 2011-02-06
Can you better describe the "bits of code?"

[http://doc.slitaz.org/en:handbook:livecd](http://doc.slitaz.org/en:handbook:livecd)

"When the loading process has finished, you can log-in to the desktop as the tux user, without any password. To use the administrator account, or root, you can start a Terminal and type the command su. The default password is root."

Boot the live CD and type "tux" for user name and then press enter for the password and see what happens.

What are the specs on this machine?  Processor speed, ram?  If it is a pentium 4 it might be able to boot off USB, but older than that it is a lot of work.

You may be able to try this:
[http://www.bodhilinux.com/about.html](http://www.bodhilinux.com/about.html)

MarshaG.

---

### Post by 4042966262 on 2011-02-06
see [http://ubuntuforums.org/showthread.php?t=1676611](http://ubuntuforums.org/showthread.php?t=1676611) for a photo i uploaded, i think the code is the same ill check tomorrow, as well as try everything else mentioned

---

### Post by 4042966262 on 2011-02-06
i don't know  Processor speed, ram etc.. how do i find it? its a old Gateway PC think it ran windows 2000. or used to.

---

### Post by Hur Dur on 2011-02-06
It looks like a kernel panic. You need to install it from floppy. To do this, you can grab the [Floppy image]("http://www.slitaz.org/en/get/index.html#floppy") and write it to a floppy. Then boot from it. A mini-tutorial is on the Downloads page. As for finding your system specs, is dxdiag present in Windows 2000? If it is, just click run, and type in dxdiag. It will give you all of your system information.

If SliTaz doesn't work, there is always [Tiny SliTaz]("http://pizza.slitaz.org/tiny/"), [blueflops]("http://blueflops.sourceforge.net/"), and if you're desperate, [BasicLinux]("http://distro.ibiblio.org/baslinux/"). However, if you have more than 64mb RAM, and at least a Pentium II, you're in luck. Arch Linux + IceWM will run in under 32mb RAM. Debian's net install + IceWM will run in under 32mb RAM. Slackware will run in under 64mb RAM. Puppy Linux, although slow, will run on 64mb RAM. KolibriOS, which is not Linux, will run well in under 16mb RAM.

---

### Post by marshag63 on 2011-02-07
It would help a lot if you could make a swap partition before booting slitaz.  Grab and burn a copy of DamnSmallLinux and use a terminal to run fdisk and create a swap partition of say 600 MB or so - if it was running with 128 MB, that should do the trick.

MDG

---

### Post by 4042966262 on 2011-02-07
i played with DamnSmallLinux. had a Ether of a time installing it. besides Slitaz is better looking. HurDur, Booting from floppy is what I'm trying to do. i don;t understand how to do it on a PC running Lubuntu that will not show me a Floppy Drive icon. and booting in Windows 2000 on the old Gateway? no can do. OS is obsolete it was removed by a tech friend somehow.

''terminal to run fdisk and create a swap partition of say 600 MB or so - if it was running with 128 MB, that should do the trick.''   <----WHA!??!

---

### Post by 4042966262 on 2011-02-07
marshag63 im curios, under your username is
Gee! These Aren't Roasted!
did you set that? and if so how? 
mine says ''5 cups of ubuntu'' which i never set?

---

### Post by 4042966262 on 2011-02-07
i think i have 64 ram. and on Boot it says Pentium II. i think if cant get Slitaz working, ill try Arch Linux + IceWM BUT im going to need help instaling it!! i have a live Cd for Arch Linux, and i installed it. and booted to a blue terminal!! login, then a blinky # sign. i was told i had to install the Desktop screen..which boggled me. 
Should i run Slitaz? or IceWm on Arch?

---

### Post by marshag63 on 2011-02-07
Okay, lets not get crazy here.  Let's stick with Slitaz - they have a loram cd you can burn and try booting.  

Remember, it is an old computer, but it can still be very useful.

Download the slitaz-loram-cdrom.iso

[http://download.tuxfamily.org/slitaz/iso/2.0/flavors/](http://download.tuxfamily.org/slitaz/iso/2.0/flavors/)

MDG
P.S. I have no idea how "Gee, these aren't roasted got there."

---

### Post by wojox on 2011-02-07
I've had trouble with SliTaz before. Tried "slitaz-cooking" and it ran fine.

---

### Post by 4042966262 on 2011-02-10
whats a loram?

---

### Post by marshag63 on 2011-02-10
loram = low ram

MDG

---

