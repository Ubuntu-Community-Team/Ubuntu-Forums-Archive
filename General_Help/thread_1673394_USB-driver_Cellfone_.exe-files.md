---
title: "USB-driver? Cellfone?? .exe-files???"
date: 2011-01-22
forum: General Help
---

### Post by mike_rider on 2011-01-22
:confused: **How do I install USB-driver for my cellfone?** 			 			 			 		   		 		 		[SIZE=4][FONT=Comic Sans MS]Dear  Linux-Experts: How do I install a driver or get Ubuntu to recognize my  USB-connected cellfone when the CD only contains a install.exe that does  not work in Linux?  :confused: What good is this platform anyway if you can´t run any of the .exe-programs out there?? And please: explain for the Linux-Newbie! 
Thank You°!  :D :guitar:
*mike[/FONT][/SIZE]

---

### Post by hakermania on 2011-01-22
OK, as I understood, you have a CD which contains the drivers for your cellphone....
But you cannot install them, they are for windows. I would recommend checking the official site for Ubuntu Drivers.

---

### Post by mike_rider on 2011-01-22
Thanks for the hint! There are so many different drivers for ubuntu that I am really lost what exactly I´ll be looking for.:rolleyes:

 Should I search for a general "USB-driver" or "cellfone-driver" - or maybe the brand of my fone (samsung)? :confused:

Please: Although I´ve worked with Computers for quite a long time now I´m really new to Linux![-o<

Thankyou again for all answers!
*mike
=D>

---

### Post by ebasa on 2011-01-22
Shouldn't need any driver just plug it in, works with every cellphone I have ever had. What are you trying to do?

---

### Post by mike_rider on 2011-01-23
Thanks for the reply, ebasa! I am simply trying to get all the photos from my cell-fone-camera on my PC. I did not find the cellfone listed as a memory-medium of any kind and it did not make any sound when I plugged it in under under ubuntu either (in Win7 it at least makes a "clonk-sound" letting me know that it does not recognize) :p

---

### Post by piquat on 2011-01-23
Hmmm, I'm far from any expert at this but if you plug it in and then type:

```
lsusb
```in a terminal, it should show if it's even seeing the device.  If it shows up, it doesn't mean it's going to work, you may still need a driver.  It only tells you if the root hub in the machine even sees it as a piece of hardware.

Good luck!

---

### Post by Mark Phelps on 2011-01-24
> **mike_rider said:**
> :confused: How do I install a driver or get Ubuntu to recognize my  USB-connected cellfone when the CD only contains a install.exe that does  not work in Linux?
Basically, you don't.  Ubuntu scans the hardware when first installed and loads all the necessary drivers.  If your cellphone won't work with the generic USB driver, you won't be able to use it with Ubuntu.

If you are plugging your phone into a USB hub, try plugging it directly into the PC itself.  That works better for some devices.

> What good is this platform anyway if you can´t run any of the .exe-programs out there?? 

The ".exe-programs" out there are for MS Windows -- and Ubuntu, like all other Linux distros, is a free ALTERNATIVE to MS Windows, not a free VERSION of MS Windows.

If you installed Ubuntu primarily to use MS Windows stuff, you'll be sadly disappointed and you wasted your time.

---

