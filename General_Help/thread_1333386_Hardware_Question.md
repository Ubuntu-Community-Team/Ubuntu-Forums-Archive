---
title: "Hardware Question"
date: 2009-11-21
forum: General Help
---

### Post by Jacob32123 on 2009-11-21
I few days ago I installed Ububtu on an old computer of mine, and I love it. I am mainly using it to host a web server, and it works great. I am looking to install it on a tablet computer of mine, currently running Windows 98 (with broken touchscreen). And right now I am having trouble getting Ubuntu on it because it has no CD drive. It has 1 PCMCIA slot, (right now used for WiFi)  1 USB port (I have a hub), IR send/receive, and that's about it. I have a 16 GB U3 SanDisk thumbdrive, but the driver doesn't install correctly, and a [http://www.fantomdrives.com/products/dvdram.htm](http://www.fantomdrives.com/products/dvdram.htm), but I can't find a driver for that. Anyone have any ideas?

- Jacob

---

### Post by lmarmisa on 2009-11-21
May be a CD/DVD USB unit would be the simplest solution.

I hate CDs and, of course, I don't want to buy one of this USB CD/DVD units.

So, when I have your problem with some of my PCs (very rarely), I have a trick.

My trick is to use an external USB hard disk (this disk is an IDE disk). So, I open the box, remove the hard disk and substitute it with an old IDE CD unit that I have.

When I finish the installation, I restore the changes in my external HD.

I don't know if this solution could help you.

Best regards,

Luis

---

### Post by Jacob32123 on 2009-11-21
Not a bad idea, I have a USB CD/DVD drive, but I need a driver
*Continues hunting for CD*


Edit:
I just thought of the fact that the driver is on a CD... Epic fail


*Goes to look for old PCMCIA CD drive*

Grr PCMCIA card is stuck in

---

### Post by lmarmisa on 2009-11-21
A Tablet PC sounds to me like a quite new computer (but it is running W98!!!).

Check if the BIOS supports USB CD/DVD drives.

Regards,

Luis

---

### Post by Jacob32123 on 2009-11-21
Agreed. In around 2001 I got to beta test a tablet computer, and I still own it. It runs 98, it only appears to support the included PCMCIA CD Drive

---

### Post by underquark on 2009-11-21
When you say the driver doesn't install correctly, do you mean a Windows 98 driver?  Have you tried putting ubuntu onto a USB stick, setting USB as the first boot option in the tablet PC's BIOS and then booting from the stick?  Don't need the Windows drivers then.

---

### Post by Jacob32123 on 2009-11-21
When I said the driver didn't install correctly, I was referring to the driver for my 16 GB USB thubdrive

---

### Post by lmarmisa on 2009-11-21
Have you checked if an update of the BIOS firmware is possible?.

In any case, take a look to the BIOS menu in order to see the boot options that it supports. Any USB device? Network?.

---

### Post by Jacob32123 on 2009-11-21
OK, under the boot settings menu, I have

Removable Devices
ATAPI CD-ROM Drive
Hard Drive
Network boot

Under hard drive I have
IBM-DJSA-205-(PM)
       Bootable Add in cards

---

### Post by lmarmisa on 2009-11-21
Do you have some type of slot for a memory card (Bootable Add in cards 	)?

No information under Removable Devices? Could it apply to a USB CD drive?

Do you know the model of your tablet computer?

---

### Post by Jacob32123 on 2009-11-21
The only thing that looks like a memory card slot is the PCMCIA slot, but I think this bios is generic
I dont know of any USB cd drives that were included, only a PCMCIA
It is a Sonic Blue Progear 1050 SE

---

### Post by lmarmisa on 2009-11-21
Try to do this test.

Define the following boot priority in the BIOS:

1) Removable Devices
2) Hard drive

And change de order of the Hard drive sub-menu:

1) Bootable Add in cards
2) IBM-DJSA-205-(PM)

Connect the USB CD/DVD driver with a bootable Ubuntu CD inside and start the system.

If Ubuntu starts, bingo!!!.

The network option is unusable because we would need a Ethernet card with PCMCIA interface.

---

### Post by Jacob32123 on 2009-11-21
So excited, something is booting....
I disabled the hard drive and I am in 98 how is this possible?!
AHHHHH

---

### Post by lmarmisa on 2009-11-21
I have fount this FAQ that could be useful:

[http://www.keyesfamily.org/WebRoot/ProGear/Filez/Docs/ProGear%201050%20FAQ.htm](http://www.keyesfamily.org/WebRoot/ProGear/Filez/Docs/ProGear%201050%20FAQ.htm)

Apparently, some kind of BIOS update is possible.

---

### Post by Jacob32123 on 2009-11-21
Thanks, that is helpful. I am getting mad at this thing. I think later I will get a pliers and rip out the PCMCIA card, then plug in the CD drive

---

### Post by lmarmisa on 2009-11-21
Jacob,

I wish you the best luck. It would be a dream to give a new live to your old tablet computer.

Please, send me a private mesage if you get any advance or if you need my help.

Best regards,

Luis

---

### Post by Jacob32123 on 2009-11-21
I made some progress. I changed the boot order, but it does not find the ISO on the CD or thumbdrive

---

### Post by lmarmisa on 2009-11-21
Hmmm...

Sorry, Jacob, but I don't understand. What is the progress? Only the change of order?.

Regards,

Luis

---

