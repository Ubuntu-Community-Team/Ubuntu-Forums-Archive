---
title: "hey! pls help me make a .iso to a live usb stick"
date: 2009-12-20
forum: General Help
---

### Post by Nailox on 2009-12-20
i made a usb stick bootable but now how to reboot and use the install on the usb? i set the boot device priority in BIOS so removable device is on first place but still doesnt work - need help with this

---

### Post by underquark on 2009-12-20
Either System...Administration....USB Startup Disk Creator or try UNetbootin [from here]("http://unetbootin.sourceforge.net/")

---

### Post by Nailox on 2009-12-20
thanks Shrek! You rock!

---

### Post by Nailox on 2009-12-21
bump - i used unetbootin but still doesnt work - pls look at the original post - 10x

---

### Post by miniyak on 2009-12-22
Ive been having a lot of issues with usb booting also

so far this is what if had the most success with 

reinstall unetbootin (precautionary)

format usb drive w/ gparted (should be in sys>admin) don't forget to unmount drive before doing this

write the 9.04 iso with unet (i have had no luck with 9.10)

ive also heard you can use virtual box to do a regular instal too... but thats if you can get usb working with vbox

Do you want to use the stick just as a live cd? (asking because ive been looking into persistence)

---

### Post by USB_NL on 2009-12-22
google: pendrive linux

good tutorials

---

### Post by miniyak on 2009-12-22
If nailox has access to a windows machine there are plenty of good solutions on pendrivelinux.com

if using window you also can try [http://www.linuxliveusb.com/]("http://www.linuxliveusb.com/")

Im running ubuntu only, finding alternate solutions to unetbootin and usb startup creator has been like finding a needle in a haystack. Nevermind the fact that i want persistence.

---

### Post by USB_NL on 2009-12-22
I think you can run the 

USB-Installer-for-Ubuntu-v0.2.exe for Ubuntu karmic koala

in wine succesfully

I dont have a usbstick to test it now

---

### Post by miniyak on 2009-12-22
hmm ill give that a try 

the .exe that the second link i provided leads to will not work with wine... but may be others will

---

### Post by Nailox on 2009-12-23
solved the problem with unetbootin - it worked - if u need the pendrive for a win machine make sure you format the pendrive in FAT32 - shall i mark the thread as solved ?

---

### Post by miniyak on 2009-12-23
sure, the solution seems to be try and try again till your usb writer of choice decides it feels like working, lol.

---

