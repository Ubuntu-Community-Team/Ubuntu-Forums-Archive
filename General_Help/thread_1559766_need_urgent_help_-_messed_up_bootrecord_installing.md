---
title: "need urgent help - messed up bootrecord installing and now I can't boot anymore"
date: 2010-08-24
forum: General Help
---

### Post by Xenphor on 2010-08-24
I guess I did something pretty stupid. I booted a live ubuntu usb and instead of installing it to the hardrive, I attemped to install it to another usb drive. Now, I have to mention, my computer doesn't natively allow booting from usb so I had to install the Plop boot loader. After I had installed Ubuntu on the other usb, I rebooted, and to my surprise it seems grub has replaced the windows and Plop bootloaders. Unfortunately, since I guess grub is looking for my usb install (and my computer will now no longer boot from usb) it simply leaves me at a grub rescue screen saying "Error no such device". 
 
I actually tried just using my recovery cd that came with my laptop and wiped the hardrive and reinstalled windows. Unfortunately, grub is still on there and won't allow me to boot. I do not have an original xp cd to try and fix the boot record.
 
Now here's an even greater problem; my computer will boot from a cd but it is extremely picky about what cd that is. It seems that it will only actually read retail grade cd's (i.e. my laptop recovery cd) and not burned cds so I can't simply just burn a recovery cd to fix the boot record. 
 
I think my computer may be able to boot using a network somehow but I have no idea how to do that. 
 
Does anybody know anything I could do to fix this?

---

### Post by wilee-nilee on 2010-08-24
Post the boot script in my signature, use a live Ubuntu cd to do this. post it in code tags as described.

---

### Post by Xenphor on 2010-08-24
I can't use a live cd because my computer won't boot from a cdr, only retail disks. I actually have an xubuntu cd that I ordered in the mail and that won't work either. Unless there is some place I could get a genuine retail grade cd and not just a cdr variant it won't work.

---

### Post by wilee-nilee on 2010-08-24
Some computers need the f-key prompt to choose the boot mine is f12. It is highly unlikely that your computer wont boot any cd, just so you know, it is knowing how to.

Lots of people get used to changing the bios to read the cd first but this does not always work.

---

### Post by Xenphor on 2010-08-24
No what I'm saying is that my computer will only boot from a cd that's a retail grade CD, not a burned CD. It is able to boot from my laptop recovery cd and that is how I wiped the drive and reinstalled windows. However, I have never been able to get it to boot or even read from any CD-R I have ever tried so I am unable to use a Linux live cd. And, as I said, even a linux cd that I ordered online will not work. Unless  you know of a place where I could get a Linux cd that is a high quality, retail grade cd then I don't believe it will work.

---

### Post by wilee-nilee on 2010-08-24
Use the plop booter to boot your USB reload it if needed. Frankly your problem is dead without more information or the ability to boot a live USB or cd.

Do you understand what the f-key prompt for choice of boot is?

---

### Post by Xenphor on 2010-08-24
Yes, as I have said, using the F-key and booting from a CD-Rom is exactly what I did to use my laptop recovery cd to install windows. I know how to boot from a cd-rom; I've done it hundreds of times. 
 
What I'm trying to say is that my computer will only boot from CDs that are **_RETAIL GRADE _**CDs. It will NOT read CD-Rs that are burned from a computer, at least none that I've ever tried. The Linux CDs that I have are NOT retail grade and therefore WILL NOT boot. I know it sounds weird but the drive on my laptop is a piece of trash apparenlty and will not accept any other type of CD. 
 
Installing the Plop bootloader requires a CD, right? One that I will have to burn myself? Then that will not work. 
 
I guess my only options are to obtain a retail WinXP disk and try to use it to fix the MBR or somehow obtain a Linux cd that will actually boot. I've ordered another Linux cd that is supposedly printed by Canonical themselves so hopefully that will work.

---

### Post by wilee-nilee on 2010-08-24
Here is a link to a XP ISO.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

It sounds like you know how to run fixmbr from the repair command.

I don't know if this helps as a retail CD seems to be needed. Personally I have never heard of that but it is possible, even though it makes no sense.

---

