---
title: "Transfer files from one computer to another"
date: 2009-10-08
forum: General Help
---

### Post by sponsoredwalk on 2009-10-08
I'm planning on getting a new laptop and am wondering if there is a way to transfer around 200gb of music, films etc... from my desktop I have now to the new laptop when I put 9.10 on at the end of October, without internet or an external hard-drive. Would it work by simply connecting a usb from one pc to the other and if so, is there a special program/settings I should worry about. Thanks(:

---

### Post by stinger30au on 2009-10-08
9.04 and 9.10 have "giver"

fireup shell and type in

sudo apt-get install giver

giver is a file sharing app for a lan that requires no setup

piece of cake to use

---

### Post by sponsoredwalk on 2009-10-08
Sorry, I should have mentioned, my internet connection goes from the internet box to the back of the laptop via a wire, no wireless.

---

### Post by sponsoredwalk on 2009-10-08
> If you use a regular "A/A" USB cable (a stardard cable with a USB connector at each end), you can fry the USB ports, their power supplies, or even a motherboard. 

I found this after a lot of googling, is it true???

---

### Post by StuartN on 2009-10-08
> **sponsoredwalk said:**
> I found tis after a lot of googling, is it true???

Apparently there is such a thing as a USB-A to USB-A (or A/A USB) cable and that is NOT what you need because it will fry two master devices. You would need a bridged USB, or USB networking cable, that contains an electronic isolating circuit between the connectors.

In any case, if both computers are connected to the same router, or if you use an ethernet crossover (gaming) cable between the two PCs, then you can simply share folders and use Nautilus, rsync or any normal file copying command. (Note: most modern and all GigaBit interfaces will detect a regular, uncrossed ethernet cable and auto-switch).

---

### Post by howefield on 2009-10-08
> **sponsoredwalk said:**
> ...am wondering if there is a way to transfer around 200gb of music, films etc... from my desktop I have now to the new laptop....(:

200 gigs ? You must be very rich....

Just buy an external drive. ;)

If you want something low cost, you could remove your existing drive and place it inside a drive caddy and connect to the new laptop via usb, (in other words, make an external drive)

Cost about 5 pounds for a cheapo 3.5 inch drive caddy.

---

### Post by sponsoredwalk on 2009-10-08
> **howefield said:**
> 200 gigs ? You must be very rich....

Just buy an external drive. ;)

If you want something low cost, you could remove your existing drive and place it inside a drive caddy and connect to the new laptop via usb, (in other words, make an external drive)

Cost about 5 pounds for a cheapo 3.5 inch drive caddy.

"Rich" - Hardly, just spent 7 years buying albums. But this seems like great idea because it's cheap However, I have a serious problem with it, if you take your existing hard-drive out, there are two issues, 

1.The size of the connection. - There are different sizes aren't there? I mean, I remember buying my extra hard-drive and being given a lecture by the sales clerk on how there are two different types, he said I was buying the disk on pure chance as I didn't know the specifications. Luckily it fit. (phew:P)

2. If I am not careful I could fry the disk due to static energy. I mean I'm not going to chance losing everything to save 20 euro-ish, Is it serious risk or am I over-cautious. 
Gratias tibi ago:)

---

### Post by howefield on 2009-10-08
> **sponsoredwalk said:**
> "Rich" - Hardly, just spent 7 years buying albums.

Was joking :)

> 1.The size of the connection. - There are different sizes aren't there? I mean, I remember buying my extra hard-drive and being given a lecture by the sales clerk on how there are two different types, he said I was buying the disk on pure chance as I didn't know the specifications. Luckily it fit. (phew:P)

Are you talking about internal drives above ? maybe IDE vs SATA ? You would need to buy a caddy that had a connection to suit your drive. Does your desktop drive have a ribbon cable about 2 inches wide connecting it to the motherboard, or is it a small cable with a connector about half an inch wide ?   

> 2. If I am not careful I could fry the disk due to static energy. I mean I'm not going to chance losing everything to save 20 euro-ish, Is it serious risk or am I over-cautious. 
Gratias tibi ago:)

Well actually, seems to me you don't mind taking a chance on losing everything, given that you do not have a robust backup of your 200 gigs in the first place, otherwise this conversation wouldn't be taking place ;)

You can use anti static straps and touch something that is grounded to discharge static, yes it is a risk but for a hard drive, I'd say it was very small. Others may disagree.

---

### Post by CharlesA on 2009-10-08
Best bet would be to get something like a 250-300GB external drive imo. Laptop drives aren't really that large (or at least mine isn't, only 250GB)

---

### Post by sponsoredwalk on 2009-10-08
Cool, thanx for the help, i'l do my best to search for the caddy, if I can't find it I'll get the wire. An external drive is useless to me as i' still have like 100GB left when I buy this new laptop and fill it up. I'll be sparing, I'll sacrifice the Michael Jackson bootlegs, should free up 20gb extra space ;) Vale!

---

### Post by Peter09 on 2009-10-08
Just connecting an ethernet cable between the two machines should work.

OR,
if your new laptop has a wireless connection, then buy or borrow a usb wireless dongle for the desktop a build a peer-peer network.

---

### Post by howefield on 2009-10-08
If the cable connecting your existing hard drive to the motherboard looks like this..

[http://www.cksinfo.com/clipart/electronics/computers/cables/ide-cable.png](http://www.cksinfo.com/clipart/electronics/computers/cables/ide-cable.png)

you need a usb caddy suitable for an IDE hard drive.

If the cable connecting you hard drive to the motherboard looks like this

[http://img.alibaba.com/photo/50641287/SATA_Cable.jpg](http://img.alibaba.com/photo/50641287/SATA_Cable.jpg)

you need a usb caddy capable of taking a SATA hard drive.


As CharlesA said however, buying an external would be the simplest way and give you a backup solution into the bargain. My solution lowers the cost, but if you want to put the drive back into your desktop for selling, ect, you still don't have a backup.

Good Luck.

---

