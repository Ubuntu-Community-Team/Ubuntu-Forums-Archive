---
title: "Ubuntu Dualboot Deactivated Windows 7 Anyone Else Experience This ???"
date: 2009-12-15
forum: General Help
---

### Post by wgilthorpe on 2009-12-15
My new laptop came with Windows 7 installed.  I decided to dual boot with Ubuntu 9.10.  Install went well everything seemed run smoothly, but; after two or three weeks of using both OSs about equally, Windows 7 says that it is counterfeit.  I do not know much about the MS verification system.  Is there any way that GRUB or Ubuntu affected that system?  I looked all over the forum and found no similar instances.  Any replies will be appreciated.

---

### Post by jocko on 2009-12-15
Ubuntu does not do anything to your windows 7. Did you get a valid windows 7 licence when you bought the computer?

---

### Post by philinux on 2009-12-15
> **wgilthorpe said:**
> My new laptop came with Windows 7 installed.  I decided to dual boot with Ubuntu 9.10.  Install went well everything seemed run smoothly, but; after two or three weeks of using both OSs about equally, Windows 7 says that it is counterfeit.  I do not know much about the MS verification system.  Is there any way that GRUB or Ubuntu affected that system?  I looked all over the forum and found no similar instances.  Any replies will be appreciated.

Probably **Windows Genuine Advantage**

---

### Post by ean5533 on 2009-12-15
> **wgilthorpe said:**
> My new laptop came with Windows 7 installed.  I decided to dual boot with Ubuntu 9.10.  Install went well everything seemed run smoothly, but; after two or three weeks of using both OSs about equally, Windows 7 says that it is counterfeit.  I do not know much about the MS verification system.  Is there any way that GRUB or Ubuntu affected that system?  I looked all over the forum and found no similar instances.  Any replies will be appreciated.

Like the guys above said, Ubuntu definitely doesn't touch your Windows install or do anything to corrupt/deactivate it. However, I've heard **plenty** of reports of Windows users randomly having their copy of windows deactivated for no good reason. The good news is that if you call up Microsoft to complain about it, they usually seem to reactivate you without too many questions. Still a pain, though.

If you call them up, let us know how it goes.

---

### Post by fahadsadah on 2009-12-15
delete this post please mods

---

### Post by fahadsadah on 2009-12-15
Could the system have been sold with unlicensed Windows? Cracked by an OEM SLP emulator, in the bootloader, perhaps?

This is the most common way of bypassing Windows 7 activation, but is overwritten by replacements of the bootloader, such as that which setting up a dualboot requires.

---

### Post by wgilthorpe on 2009-12-15
I don't think that the bootloader was messed with.  I bought it from Newegg.com.  I will try and call them (Microsoft) now.  I just hope they are not closed for business yet today.

---

### Post by wgilthorpe on 2009-12-15
I called Microsoft and got a new license number with surprisingly little hassle.  I believe this may be a bios or system time in cmos issue.  When I first did the dual boot install, i noticed that the time in windows was wrong so i told it to update the time over the net.  Then when i booted ubuntu that time was wrong.  so i told it to update on the net.  this happened two or three times before i set the time manually on both and set them not to update the time automatically.  I read a few posts on other sites that if windows time is messed up the wga can fail.  My problem is solved, but i would still like to know if anyone else has experienced anything like this.  Thanks for your replies.

---

### Post by fahadsadah on 2009-12-17
You'll need to change the motherboard battery.

If you are not confident opening the machine, the manufacturer can change the battery for you

---

### Post by northern lights on 2009-12-17
> **fahadsadah said:**
> You'll need to change the motherboard battery.Nopes. Most likely UTC/LT issue - [https://help.ubuntu.com/community/UbuntuTime]("https://help.ubuntu.com/community/UbuntuTime")

---

