---
title: "Quick help! Move Wubi install from C: to USB!"
date: 2009-11-16
forum: General Help
---

### Post by DrMarcusAurelius on 2009-11-16
I have a Wubi install of Ubuntu 9.1 on my C: drive.  There are instructions on how to move that to a USB drive so that it is bootable here:  

[http://www.pendrivelinux.com/move-wubi-ubuntu-install-to-an-external-usb-drive/](http://www.pendrivelinux.com/move-wubi-ubuntu-install-to-an-external-usb-drive/)

The problem is that when I get to step five there is no file "menu.lst" on the USB.  In fact, there are no files in the folder "Grub" (on the USB) at all.  Also, when I look in the file "boot" (on the USB) there are no files, only the folder "Grub".  

I greatly appreciate any help with this.  I know that I could simply create a Live USB with the Live USB tool and I know that I could try to do a full install directly to the USB.  For various reasons, however, I want to be able to move my existing Wubi install and use it from a USB.  Help!

Thanks in advance

---

### Post by P4man on 2009-11-16
ubuntu 9.10 uses grub2 instead of grub. Im not familiar enough with wubi to tell you exactly what to do, but you wont find a menu.lst for grub2. You should find a grub.cfg somewhere though

---

### Post by DrMarcusAurelius on 2009-11-16
P4Man,

When I boot from a Live CD and look in the folder "boot" on my C: Wubi install, nothing shows up except for the folder "grub."  And when I look in that folder, nothing shows up there either.  But when I boot up from the Wubi install and look in those two folders, they are populated.  One thing I tried is to then simply copy and paste the files in those folders to the corresponding folders on the version I copied to my USB.  But the file "grub.cfg" says not to edit it because it is automatically generated.  Nevertheless, I've tried to edit it but I'm not quite sure how.  I tried using root=LABEL=USB but that didn't work.  When I put the USB into a different computer and boot from the USB drive I'm get the prompt to choose between XP or Ubuntu but when I choose Ubuntu it says that there was an error and that I need to load the kernel first. I'm very much a novice, so I appreciate all the help  I can get.  Thanks

---

### Post by wrgb2 on 2009-11-16
This might help you : [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by DrMarcusAurelius on 2009-11-16
wrgb2

Thanks for this.  Last time I checked it I couldn't find anything specific to the Wubi setup.  I'm certainly willing to learn new stuff, but I'm very reluctant to mess with grub.  When I tried to do a complete install just to my USB drive it messed up the boot member on my c: drive and caused me some huge headaches.  I was hoping this wouldn't be too hard.  The initial instructions (that are now out of date) made it seem quite simple.  Thanks

---

### Post by DrMarcusAurelius on 2009-11-16
any other ideas?

---

### Post by Shmi on 2009-11-19
Hi Dr, 

for one - on Ubuntu 9.10 the grub files are withing the virtual disk itself, where as with the previous versions the files are on 'c:\ubuntu\disk\boot\grub\' (if you install to that particular folder). 

I suspect what you would need to do is to edit the wubildr.mbr (which is a grub4dos file) on you flash drive to find the root.disk in different location (on your flash) - as it is pointing to the 'c:\ubuntu\disk\root.disk' at the moment (again, if you installed to that folder). Keep in mind - I am not even 10% sure about this, so please be careful before playing with this - but from what I have researched this is the situation. 

I am currently investigating / researching something similar, will post new info for you as I find it.

---

### Post by DrMarcusAurelius on 2009-11-19
Shmi,

Yes, you are correct that the relevant grub files are now within the virtual disk itself.  I will look into your suggestion.  Can I use a text editor to edit the wubildr.mbr or will I need another program?  Let me know what you find and thanks for your help

Marcus

---

### Post by Shmi on 2009-11-20
Hi there, 

from what I can pick up, you must use a hex editor to set the file straight. 

I'm just WAAAAAYYYYY to dumb to understand how the hex editor work.

---

### Post by Shmi on 2009-11-20
Ok, I would suggest Hex Workshop Hex Editor - although you can use other if you feel inclined to.

I found the detail I needed in the wubildr installed by wubi 8.04, but I can't find the info we need in wubildr installed by wubi 9.10 - but at least some progress.

---

### Post by DrMarcusAurelius on 2009-11-20
I don't understand why one would have to edit wubildr to do this with 9.10 when it was not necessar for 9.04. Surely there is someone here who knows enough to answe this. Thanks in advance

Marcus

---

