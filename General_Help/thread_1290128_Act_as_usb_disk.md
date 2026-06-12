---
title: "Act as usb disk"
date: 2009-10-13
forum: General Help
---

### Post by posterberg on 2009-10-13
I am wondering if anyone knows of a driver that can make a usb port on my linux box to act as a usb disk, so that another computer that connects to it will see it as a usb drive.

Would be great if it also good make it look to be FAT32 formatted on the fly...

i.e. folder /home/user/usb_emultaded_disk will show up as as the root folder on the other computer as a FAT32 disk.

This would :guitar: for my non-network-enabled stupid TV as it plays most things from USB drives.

YES, I already have xbmc running on the Linux box but it would be nice to also be able to use the built in media functionality in the TV... ;)

---

### Post by 3rdalbum on 2009-10-13
As far as I know, this is technically impossible on ordinary USB ports. You would end off short-circuiting your TV and USB controller.*

There is a type of USB port that can be used as either host or device, but unless your computer is a BeagleBoard you don't have one.

* In fact, I think the sale of USB A-to-A cables should be strictly controlled, and the USB-IF organisation should sue any device manufacturer that uses the USB logo and has their device connecting with an A-A cable.

---

### Post by dandnsmith on 2009-10-13
If you google for "usb network linux" you'll find several links to networking and usb (which is what you need)

It is important to remember that you need a cross-over usb cable to connect the two PCs - the standard one is useless, and it would connect read-read, and write-write.

HTH

---

### Post by posterberg on 2009-10-13
> **dandnsmith said:**
> If you google for "usb network linux" you'll find several links to networking and usb (which is what you need)

It is important to remember that you need a cross-over usb cable to connect the two PCs - the standard one is useless, and it would connect read-read, and write-write.

HTH

Hmm, usb network sounds like networking... I need it to act as a disk and not as a network port...

---

### Post by posterberg on 2009-10-13
> **3rdalbum said:**
> As far as I know, this is technically impossible on ordinary USB ports. You would end off short-circuiting your TV and USB controller.*

There is a type of USB port that can be used as either host or device, but unless your computer is a BeagleBoard you don't have one.

* In fact, I think the sale of USB A-to-A cables should be strictly controlled, and the USB-IF organisation should sue any device manufacturer that uses the USB logo and has their device connecting with an A-A cable.

Wouldn't it be possible if I use a cross-over cable? Does the hardware actually control what signals is sent on the cable? Can't any signaling on the wire be emulated? I do understand that you need to make a cable that won't short circuit things...

---

### Post by P4man on 2009-10-13
Perhaps you could look at buying a cheap NAS with USB. Hook it up to the tv through  USB, and it would look like a USB drive to the tv (I guess), and hook it up on the LAN at the same time, so your PC can read/write to it. Well, Im actually not 100% sure thats possible, but sounds like worth looking in to :)

---

### Post by justleen on 2009-10-13
> **posterberg said:**
> Wouldn't it be possible if I use a cross-over cable?.

There is no such thing as an USB-crossover cable...

---

### Post by posterberg on 2009-10-13
> **justleen said:**
> There is no such thing as an USB-crossover cable...

MMmm, no but one could be made I suppose... I would believe isn't it just a matter of making the ports electrically compatible. How hard can that be?

There doesn't seem to be any electrical differences on the computer and the disk side according to this page; [http://pinouts.ru/Slots/USB_pinout.shtml](http://pinouts.ru/Slots/USB_pinout.shtml)

Doesn't this mean that I could solder my own cross-over cable if I wanted to?

---

### Post by prshah on 2009-10-13
> **posterberg said:**
> can make a usb port on my linux box to act as a usb disk, so that another computer that connects to it will see it as a usb drive.

You can take a look at this thread [Mass Storage Emulation]("http://forums.linuxfordevices.com/embedded-linux-questions-answers-f3/mass-storage-emulation-t1068.html") but i don't know how useful it will be for you..

You can also take a peek at [Linux-USB Gadget API Framework]("http://www.linux-usb.org/gadget/")

---

### Post by justleen on 2009-10-13
because there is no difference in the cabling on either side does noet mean you could swap them around.. network != usb
The only thing I know that comes close to what you want, is MacOSX, which can use other Macs as external disks, which OSX does it over firewire

---

### Post by posterberg on 2009-10-13
> **prshah said:**
> You can take a look at this thread [Mass Storage Emulation]("http://forums.linuxfordevices.com/embedded-linux-questions-answers-f3/mass-storage-emulation-t1068.html") but i don't know how useful it will be for you..

This looks very interesting, thank you! I'll have a look at it later on.

---

### Post by justleen on 2009-10-13
from that page: > and the drivers/usb/gadget/file_storage.c driver is responsible for the file storage emulation appearing to **the host** as a disk drive..
I dont think that will help you... Sorry to be so negative, but I really think it cant be done the way you intend it.

---

### Post by posterberg on 2009-10-13
> **justleen said:**
> because there is no difference in the cabling on either side does noet mean you could swap them around.. network != usb
The only thing I know that comes close to what you want, is MacOSX, which can use other Macs as external disks, which OSX does it over firewire

You can use firewire this way with more than MacOSX. I've used this myself plenty of times for remotely dumping a computer's RAM =) Nice way to get around screen saver, dump memory resident passwords etc. ;)

I agree with you, it doesn't mean you can. But it should be possible to make the cable if the computer and disk side look the same. This must mean that I won't fry anything if I make a cable that way. They would as a next step of course be able to communicate...

Does the driver chip in the port prevent me from signaling whatever I want on the port? If not, shouldn't it then be possible to signal something that makes me look like a disk and not a computer? Or does the hardware kill this possibility?

I haven't looked deep in USB-specs myself so I can't say anything on the subject really. But I don't really understand why it shouldn't be possible from what have been said in this tread so far. Please tell me if you know why, then I don't need to hunt for ghosts any more... ;)

---

### Post by CharlesA on 2009-10-13
I believe you would need a [Bridged USB Cable]("http://www.hardwaresecrets.com/article/248") to do that. I don't know if the tv will see it as a regular drive tho.

---

### Post by justleen on 2009-10-13
Even if you'd manage to get a non-frying cable, then im unsure on how you would get a disk "served" on your USB port.. How would you tell your system to "mount" a disk on the USB port so you tv could pick it up as a drive?
You can't hook up a disk to that USB port (that would effectivly create a usb disk?), and you cant (by my knowledge) tell linux to share a disk TO a usb port..
I just cant see how it would work..

---

### Post by posterberg on 2009-10-13
> **justleen said:**
> Even if you'd manage to get a non-frying cable, then im unsure on how you would get a disk "served" on your USB port.. How would you tell your system to "mount" a disk on the USB port so you tv could pick it up as a drive?
You can't hook up a disk to that USB port (that would effectivly create a usb disk?), and you cant (by my knowledge) tell linux to share a disk TO a usb port..
I just cant see how it would work..

This is my exact and original question... Does anyone know of a driver that will do this?

You tell me it is impossible, it's not impossible just because no-one has yet created such a driver. I don't see why it wouldn't be possible to make one, and I was hoping, with my question, that someone here would know about one... ;)

---

### Post by justleen on 2009-10-13
Yes, I realize that that is the question.. and my answer is, I dont think you can :)

---

### Post by posterberg on 2009-10-13
> **justleen said:**
> Yes, I realize that that is the question.. and my answer is, I dont think you can :)

Would you care to help me understand why you think so? You might absolutely be right when you say that none exist, but I don't see the technical impossibility in making one. Please help me understand why if you know.

---

### Post by P4man on 2009-10-13
> **posterberg said:**
> Would you care to help me understand why you think so? You might absolutely be right when you say that none exist, but I don't see the technical impossibility in making one. Please help me understand why if you know.

an usb controller controls the USB ports. You cant just change it with software to make it behave like a different device with different firmware. Its not a fully programmable controller. Its designed to work as a hub, it has that hardwired in the controller,  and thats what it does, and no amount of tinkering will make it behave like something else. 

The only thing you could do is find a USB peripheral, not just a cable, that connects to 2 hubs simultaneously (on your tv and on your  pc), and pretends to be a removable storage device on the usb side, and something networking on the other. I don't think its impossible to build that, but I havent seen it. Closest thing to it, is like I posted earlier, a USB enabled NAS.

---

### Post by posterberg on 2009-10-13
> **P4man said:**
> an usb controller controls the USB ports. You cant just change it with software to make it behave like a different device with different firmware. Its not a fully programmable controller. Its designed to work as a hub, it has that hardwired in the controller,  and thats what it does, and no amount of tinkering will make it behave like something else. 

The only thing you could do is find a USB peripheral, not just a cable, that connects to 2 hubs simultaneously (on your tv and on your  pc), and pretends to be a removable storage device on the usb side, and something networking on the other. I don't think its impossible to build that, but I havent seen it. Closest thing to it, is like I posted earlier, a USB enabled NAS.

That makes sense, thank you!

---

### Post by justleen on 2009-10-13
I think so because of the way USB works. USB device pass through a USB Hub. That hub cant serve the connected hosts to the ohter side.

EDit: Too late, what  P4man says ;)

I would seriously consider a cheap NAS with network and usb.. Hook up the usb side to the tv, network to the PC.. That would accomplish what you want off the shelve..

---

### Post by dandnsmith on 2009-10-13
> **posterberg said:**
> Hmm, usb network sounds like networking... I need it to act as a disk and not as a network port...

Yes, it is indeed networking, but you end up being able to view the one HDD from the other PC, manipulate files and so forth (once you've sorted the permissions), and it can be made to look like just another HDD one the PC from which you view. It's rather like an NAS, but you have the setting up of it.

---

