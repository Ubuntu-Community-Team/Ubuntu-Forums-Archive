---
title: "Desperate need of help creating windows startup disk!!"
date: 2011-06-20
forum: General Help
---

### Post by javajames97 on 2011-06-20
I have the windows 7 install iso but no windows computers! startup disk creator only lets me use ubuntu variants. I have a mac and ubuntu 10.10, and i have so far found no way to write an ISO to a disk without paid windows applications like ultra ISO, its driving e ******* crazy, every time i want to write an ISO to a USB stick i need windows! and now i have a virus (trust windows)! Why can we only write .iso files to a disk in this world??? AAARRRRRRGGGGGGGGGHHHHHHHH!!!!!!!

Can someone please point me in the direction of modern civilisation, were i can write an ISO to a pendrive for FREE with linux or mac

oh and i forgot to mention, im a sensible human being, so i dont have a disk drive - im not booting to the mac

---

### Post by haqking on 2011-06-20
have you made your USB bootable ?

you cant just burn a CD/DVD .iso and burn it directly to a USB.

Please anyone else feel free to correct me though ?

however is this what you are looking for ? [http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by javajames97 on 2011-06-20
USB sticks can very well be made bootable, in the past i have spent hours but it is possible, but that was with windows, now i have nothing to work with

will check that link out though

---

### Post by javajames97 on 2011-06-20
[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

This is the main punch line, will mark as solved if this works, thank you for your help!

---

### Post by haqking on 2011-06-20
> **javajames97 said:**
> USB sticks can very well be made bootable, in the past i have spent hours but it is possible, but that was with windows, now i have nothing to work with

will check that link out though


I know they can be made bootable, it is pretty easy, i was asking if you had done.  What i was saying is you cant just burn a .iso straight to a USB drive and boot from it.

hope the link helps

---

### Post by javajames97 on 2011-06-20
well, /*no burning is strictly a disk thing*/ - i mean, i wasn't saying that i would burn, i was saying to write, which is what the other iso burners call it, but thank you, that link has shed light on my world, you really don't know how much time i have wasted on trying to get ISO files onto a memory stick, jesus christ, i actually love you man. that software is insane

does it work with all OS'?

---

### Post by haqking on 2011-06-20
> **javajames97 said:**
> well, /*no burning is strictly a disk thing*/ - i mean, i wasn't saying that i would burn, i was saying to write, which is what the other iso burners call it, but thank you, that link has shed light on my world, you really don't know how much time i have wasted on trying to get ISO files onto a memory stick, jesus christ, i actually love you man. that software is insane

does it work with all OS'?


well for the most part as long as the USB is bootable it is about extracting the files from an .iso and placing them on the USB, there may be config changes per OS but there is a page somewhere on the net for just about every OS on a pendrive these days, ever since the loss of the ever so trusty 3.5" ;-)

good luck

---

### Post by gizmo720 on 2011-06-20
you can try using dd. In the terminal, type dd if=/path/to/file.iso of=/dev/sdb. That should copy the iso right onto the flash drive (confirm you have the right device first). Although I am not sure how bootable this is. I have only used this method to create an iso from a disk and to make backups of my hd.

---

### Post by haqking on 2011-06-20
> **gizmo720 said:**
> you can try using dd. In the terminal, type dd if=/path/to/file.iso of=/dev/sdb. That should copy the iso right onto the flash drive (confirm you have the right device first). Although I am not sure how bootable this is. I have only used this method to create an iso from a disk and to make backups of my hd.

interesting...

maybe this will help then

[http://serverfault.com/questions/6714/how-to-make-windows-7-usb-flash-install-media-from-linux](http://serverfault.com/questions/6714/how-to-make-windows-7-usb-flash-install-media-from-linux)

---

### Post by Monotoko on 2011-06-20
If I understand correctly, you are trying to load Windows 7 onto a USB installer? You can try to run a simple version (XP perhaps) of Windows from a virtual machine (virtualbox), then load Windows 7 onto a USB stick using this: [http://technet.microsoft.com/en-us/magazine/dd535816.aspx](http://technet.microsoft.com/en-us/magazine/dd535816.aspx)

---

### Post by Mark Phelps on 2011-06-21
> **Monotoko said:**
> If I understand correctly, you are trying to load Windows 7 onto a USB installer? You can try to run a simple version (XP perhaps) of Windows from a virtual machine (virtualbox), then load Windows 7 onto a USB stick using this: [http://technet.microsoft.com/en-us/magazine/dd535816.aspx](http://technet.microsoft.com/en-us/magazine/dd535816.aspx)

That link shows how to create a USB stick to INSTALL Win7.  I believe that what the OP wants is to RUN Win7 from a USB  stick -- which, according to the folks at sevenforums.com, can NOT be done.

---

### Post by haqking on 2011-06-21
> **Mark Phelps said:**
> That link shows how to create a USB stick to INSTALL Win7.  I believe that what the OP wants is to RUN Win7 from a USB  stick -- which, according to the folks at sevenforums.com, can NOT be done.

there is a workaround though

[http://forum.thewindowsclub.com/windows-tips-tutorials-articles/28192-how-install-carry-windows-7-your-usb-flash-drive.html](http://forum.thewindowsclub.com/windows-tips-tutorials-articles/28192-how-install-carry-windows-7-your-usb-flash-drive.html)

---

### Post by javajames97 on 2011-06-23
A) unet bootin worked fine (thanks - )

B) i think i explained in the description??? - i have parallels, but it's useless with only 2gb ram - and the darwin+osX to run. I was looking for a way to make it easy

cheers

---

