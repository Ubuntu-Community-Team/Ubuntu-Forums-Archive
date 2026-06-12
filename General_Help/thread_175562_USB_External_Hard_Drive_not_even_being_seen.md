---
title: "USB External Hard Drive not even being seen"
date: 2006-05-13
forum: General Help
---

### Post by benuski on 2006-05-13
I just bought a 250 GB Western Digital My Book external hard drive, and it isn't getting seen by my operating system.  When I plug it in, nothing happens.  I go to the terminal and type in "lsusb" and all four slots show up blank.  Any help you guys could give would be great.

---

### Post by JoeMetal on 2006-05-13
Is it seen by any other os?

---

### Post by benuski on 2006-05-13
Windows sees it pretty much all the time, but sometimes when I plug it in it recognizes that there is a USB device, but not what kind it is.

---

### Post by brandon moore on 2006-05-13
i've had this problem for a while.  i'm hoping it'll be fixed w/dapper but it hasn't been fixed so far.  the workaround i've found is to do this:

> sudo modprobe -r ehci_hcd

then plug in your usb drive.  see if it works!

---

### Post by benuski on 2006-05-13
[QUOTE=brandon moore]i've had this problem for a while.  i'm hoping it'll be fixed w/dapper but it hasn't been fixed so far.  the workaround i've found is to do this:



then plug in your usb drive.  see if it works![/QUOTE]

Hmm... i tried that and it didn't seem to do anything...  any other suggestions?

---

### Post by benuski on 2006-05-13
I probably should have said this earlier, but when I first tried to install Ubuntu, I wanted to install it to the external hard drive, but it couldn't recognize the HD then either.  When it was trying to read for it, it gave an Error -110.  Does anyone know what that means?

---

### Post by brandon moore on 2006-05-13
what's the file system on this hard drive? (ntfs?  reiser?  ext3?)  that may have something to do with it... if it's ntfs, linux can read, but not write.

---

### Post by ahallubuntu on 2006-05-13
What kind of computer is this in?  Any idea what kind of chipset or USB card it has?  When I was first building a Ubuntu server last year, it needed a USB 2.0 card so I could plug external HDs in.  The first one I tried was a cheap PCI card with a VIA chipset.  I could not get a driver to work, even though there was supposedly support for it.  After blowing a few hours on it, I simply returned the VIA card and got an NEC-based USB card instead, at a cost of about an extra $8.  But it worked perfectly and has ever since.

So you might consider this as one option:  getting a new USB card for the computer.  Just a thought.

---

### Post by benuski on 2006-05-13
I did an lspci command in the terminal, and then this is what popped out

> :~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 0 3)
0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 03 )
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Contro ller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4 -L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem  Controller (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 420 0 Go AGP 8x] (rev a1)
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabi t Ethernet (rev 01)
0000:02:01.0 CardBus bridge: Texas Instruments: Unknown device ac47 (rev 01)
0000:02:01.1 CardBus bridge: Texas Instruments: Unknown device ac4a (rev 01)
0000:02:01.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 802b
0000:02:01.3 System peripheral: Texas Instruments: Unknown device 8204
0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless  LAN Controller (rev 02)


Does that help?

---

### Post by benuski on 2006-05-14
So I decided to return the Western Digital hard drive and got a Seagate one instead, and it worked the very first time I plugged it in.  So I guess the Western Digital just didn't like me, and now the Seagate works great! :)

---

### Post by ahallubuntu on 2006-05-14
Hmm.  OK, so you have a laptop and an Intel chipset.  That is pretty standard and should be well supported.  You would still have the option of adding a Cardbus USB2 add-on card to your laptop and plugging the hard drive into that and see if it works, but I admit that is a last resort and undesirable.  But it would at least elminate a few other guesses at potential problems and narrow it down to your built-in USB port.

I would also try to see if you can find some other software you can boot on this laptop that might detect a hard drive on one of the USB ports.  For example, I have True Image from Acronis (a Windows app), and it allows me to make a rescue CD that you can boot.  I've used this to backup/restore stuff via USB and external hard drives, so I can use that to see if my hardware really supports  external drives, elminating any software issue.  You might find some free utility (ultimate boot cd?) that does the same sort of thing.

You might also try a Unbuntu Live boot CD on another computer and plug the drive in there and see if it is detected.  If so, then that means other hardware and Ubuntu are detecting it, so probably a hardware thing with your laptop.  (Though the Ubuntu Live boot CD isn't exactly the same thing as an install, I'm told.)

Also - can you plug any other USB devices into the laptop and have Ubuntu detect them properly?

Oh, I just remembered to ask: is this HD self-powered by chance (no power cable to the drive, just USB to power it)?  If so, could be an issue with the laptop not supplying enough power to make the drive work.  Some laptops unfortunately don't.  Maybe that's why it worked on another machine in Windows.

---

