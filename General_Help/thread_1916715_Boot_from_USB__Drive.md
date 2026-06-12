---
title: "Boot from USB  Drive"
date: 2012-01-28
forum: General Help
---

### Post by nsivin on 2012-01-28
I have two PC’s, an End PC Noise workstation and a  IBM Thinkpad X60 laptop, both bought about 5½ years ago, and both running WinXP. What I have been trying to do is get them to boot Ubuntu from a USB thumb drive (I have no trouble booting from a live CD). I have set the boot menus for both of them to put removable drives first. I first tried making a bootable USB drive myself, but that didn’t work. I finally bought a bootable USB drive from pendrivelinux.com, but it doesn’t work either. Is the problem that the BIOS on these two computers is too old to actually boot from a USB drive? Is there anything I can do about it?

---

### Post by WasMeHere on 2012-01-28
Hi,

I have a Thinkpad T41, it is even older. When available, I boot from CD, which usually works out of the box. I will try booting off some USB drives, to see how it works. In the meantime, maybe you can explain why you want USB, when it works to boot from CD.

---

### Post by Rodney9 on 2012-01-28
You have to set the bios in each computer to boot from USB.
For the laptop press f2 to get into the bios for the others try f2 or f12 maybe.

Rodney

---

### Post by BC59 on 2012-01-28
> **nsivin said:**
>  Is the problem that the BIOS on these two computers is too old to actually boot from a USB drive? 

Yes
> Is there anything I can do about it?
Look here 
[http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/)

---

### Post by Indie Media on 2012-01-28
What did you mean by saying "it doesn't work" ?

---

### Post by Rebelli0us on 2012-01-28
New PCs boot from USB but older ones may not. Try a simple Win98 boot disk to see if it works. Running from USB2 is slow, it's OK if you want a portable OS.

---

### Post by WasMeHere on 2012-01-28
Hi again,

My old T41 does boot from a Transcend USB 3 stick and a slower Sandisk Cruzer USB 2 stick with a persistent Linux Mint 11 and Lubuntu 11.10. Both sticks boot OK. The USB 3 stick boots faster and a volatile system boots much faster than a persistent one. The persistent system on the USB 2 stick was much slower than boot from a CD, so it is slow but works :KS

First I pressed the 'Access IBM' button, then 'F12' to get a menu, where the USB boot drive is recognized, so I selected it and then I just waited until the whole persistent system was booted.

Normally I run Ubuntu 10.04 LTS on that computer, but Lubuntu and Linux Mint seem OK. No boot options were necessary. I use standard settings of Unetbootin (standard version from Ubuntu 10.04) except that I have added persistence. The graphics is OK and both systems even find the wifi access points around here. So I would say the hardware is still going strong.

Having fun finding out
Olle

---

### Post by nsivin on 2012-01-31
Olle’s comments were very helpful. I have tried both the PLoP and Unetbootin fixes, but they don’t make either computer boot from the USB drive. Since I long ago reset the boot order in the BIOS to put removable drives first, I have to assume that my 6-year-old BIOSes need to be updated.
 
As for why I want to boot from the USB drive, booting and running Linux from a Live CD drive is painfully slow, and I don’t know of any way to save my customizations. Since I use a portrait monitor on the desktop, etc., saving them is highly desirable.

---

### Post by WasMeHere on 2012-01-31
I suggest that you make a dual boot system, if there is space for it on your hard disk drive. Alternatively, that you replace Windows with Lubuntu or Xubuntu (booting and installing to the HDD from a live CD). Then your computers will be revitalized :-)

---

### Post by kooldino on 2012-01-31
Did you try formatting the USB drive in windows?

I've had this problem before and sometimes that solves it. 

Also, sometimes there's some program that I've had to run to format it correctly before it's bootable.

---

