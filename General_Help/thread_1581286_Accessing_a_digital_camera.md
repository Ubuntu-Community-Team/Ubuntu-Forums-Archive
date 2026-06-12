---
title: "Accessing a digital camera"
date: 2010-09-24
forum: General Help
---

### Post by ki4jgt on 2010-09-24
I have a digital camera which does not seem to have a drive, yet can hold around 15 photos. The windows software included with it allows Windows to access the photos, but I want to access them with Ubuntu. It has a USB port.

---

### Post by adwhitenc on 2010-09-24
I would look into installing [wine]("http://www.winehq.org/"), a windows application emulator. But make sure to check if the soft ware works on[ http://appdb.winehq.org/]("http://appdb.winehq.org/"). 

My camera usually just auto connects to the OS regardless. What camera do you have?

Thank you for using Ubuntu

---

### Post by coffeecat on 2010-09-24
> **ki4jgt said:**
> I have a digital camera which does not seem to have a drive, yet can hold around 15 photos.

That's not many photos. Are you sure it doesn't have a low capacity SD card in it? Can you put a flash card in it? What is the make and model?

> **ki4jgt said:**
>  The windows software included with it allows Windows to access the photos, but I want to access them with Ubuntu. It has a USB port.

Most (all) cameras come with a suite of Windows software. You don't have to use it. I would imagine that most Windows users don't use it. What happens when you simply plug the camera into Ubuntu. Whatever functionality is provided by the supplied Windows software will be available in various Ubuntu apps. Better that than messing around with wine.

The software that came with my camera was a triumph of gloss and glitz over substance. You're better off with "proper" software for image manipulation and photo management.

Video software might be another matter.

---

### Post by lisati on 2010-09-24
My experience of digital cameras (two stills cameras from different manufacturers and a HDD-based camcorder) suggests that you should be able to connect your camera via USB and access the photos without the need for the software which came with the camera.

As someone else has asked, what make and model camera are you using?

---

### Post by ki4jgt on 2010-09-24
Yes, I can put a card into the camera. and not all cameras are plug and play. I've dealt with three digital cameras in my life one plug n play and the other two required software to use. (I hate those.) The first digital camera I ever got required software. That's why I got rid of it. The second one, a plug and play I loved like crazy, but it's now 7 years old and only 4 mpixils. The new one my father got unfortunately isn't plug and play either. He got it from Walmart I believe it was a Kodak EasyShare CD82

**EDIT: There is a USB port, but it's not plug and play.
**EDIT: and when I just plug it in, nothing happens. Windows won't even access it when it is simply plugged in. The software is required for Windows to even be able to detect it. and like I said earlier, this is not the first camera I've had like this, but I haven't found any software for linux to handle one of these cameras.

---

### Post by Autodave on 2010-09-24
> **ki4jgt said:**
> Yes, I can put a card into the camera. and not all cameras are plug and play. I've dealt with three digital cameras in my life one plug n play and the other two required software to use. (I hate those.) The first digital camera I ever got required software. That's why I got rid of it. The second one, a plug and play I loved like crazy, but it's now 7 years old and only 4 mpixils. The new one my father got unfortunately isn't plug and play either. He got it from Walmart I believe it was a Kodak EasyShare CD82

**EDIT: There is a USB port, but it's not plug and play

I have 2 Kodak cameras and they both just hook right into the computer w/o any software being installed.  Have you actually tried just plugging it in and see what happens yet?

---

### Post by Autodave on 2010-09-24
> **Autodave said:**
> I have 2 Kodak cameras and they both just hook right into the computer w/o any software being installed.  Have you actually tried just plugging it in and see what happens yet?

"Plug and play" is a Windoze thing.......plug your camera in and see if Linux recognizes it.

---

### Post by Autodave on 2010-09-24
**EDIT: There is a USB port, but it's not plug and play.
**EDIT: and when I just plug it in, nothing happens. Windows won't even access it when it is simply plugged in. The software is required for Windows to even be able to detect it. and like I said earlier, this is not the first camera I've had like this, but I haven't found any software for linux to handle one of these cameras.[/QUOTE]

Windows does not recognize either of my cameras w/o the software installed, but Ubuntu recognizes both of them with no software installed.

---

### Post by ki4jgt on 2010-09-24
Sorry I'm running on no sleep. I have already tried plugging it into Ubuntu. It wont work. Nothing pops up on the desktop. Nothing comes up in the computer folder.

**EDIT: I'm trying to access the onboard memory in the camera, not the SD card. remove the SD card from yours and take a photo.

---

### Post by Hobgoblin on 2010-09-24
> **coffeecat said:**
> That's not many photos. Are you sure it doesn't have a low capacity SD card in it?

A lot of digital cameras now come with a small amount of built in storage instead of being supplied with a minuscule memory card as they were in the past.

As has been said, just try connecting it up.  Almost (but not) all digital cameras will appear as an external drive.  They will do the same under Windows, you don't need the manufacturers software.

[edit] Seems I type too slow.

What make/model camera is it?

It's very doubtful Wine will help as it will be a driver issue.

---

### Post by ki4jgt on 2010-09-24
Kodak EasyShare CD82 and like I said, this isn't the first camera I've had like this. There is no drive showing up on the computer like normal cameras. Trust me, my entire family is computer ignorant. I've had to deal with every family members camera, at every event the family has ever had. If you think I'm installing all that software on my computer you're mistaken. I understand that most cameras these days work like flash drives but this one doesn't. This isn't the first one I've seen like this, and it won't be the last. Walmart and the Dollar General both sell cheapos which require software to access the onboard memory (They don't have SD cards though)

---

### Post by arvevans on 2010-09-24
Not an expert here but you seem to be getting a lot of opinion and "mine worked" stories but not much real help.  So, I'll make a stab at some limited troubleshooting:

[LIST=1]
[*]Is your camera interface via USB (most are, but there are still a few ancient serial port units floating around).

[*]Assuming it is a USB connected camera, try opening a terminal screen and enter this command "lsusb" followed by hitting ENTER.  That should show you if the OS is actually seeing your camera as a USB connected device, and what model device it thinks it is.  Using the camera type info recovered from the lsusb command you can now start to do some googling to see what Linux interface might work with your camera.  Try the Linuxc Compatibility listing Camera sections first.  There are several generic utility camera interfaces that can be installed.

You can also do searches for "Camera" on the Ubuntu and/or Debian web support groups to see if someone else has already experienced and solved problems with your specific model camera.

Hope this helps get you started in the right direction.

[/LIST]

---

### Post by arvevans on 2010-09-24
Okay...just did some more looking at your Kodak EasyShare CD82 camera specs.  It has 16 MB of internal memory and provisions for plugging in an additional SD memory card.  The image file compression format is JPEG, DCF, or EXIF 2.21, all of which Linux should work with.  The default image file format will probably be jpeg.  

You do have to have batteries in the camera for the computer interface to work.  Not sure why it won't take power from the USB cable, but it apparently does not.

If you have fspot photo manager installed, this should automatically launch when the camera is plugged in.  If you select "CANCEL" from the fspot startup, you will still have an external memory icon appear on your desktop.  Click on this icon and you should see your camera automatically mounted as an external memory device.  Cluck on the DCIM icon within the external memory screen and you will then see yet another memory device icon.  Click on this and you should see all your image files as being on an external USB memory drive.

    or

you can just let it go into fspot and use that tool to manage your camera image files.

K7HKL

---

### Post by PhilGil on 2010-09-24
> **Hobgoblin said:**
> A lot of digital cameras now come with a small amount of built in storage instead of being supplied with a minuscule memory card as they were in the past.
That is correct. The camera the OP has will also take SD/SDHC cards.

If Linux won't recognize the internal memory then don't use it (it's too small to be very useful anyway). Offload the photos you've already taken using a Windows machine (a friend or family member must have one you can use).

Buy yourself an SD card and a card reader (they're very inexpensive or you may already have one built into your computer). In the future you should have no problems accessing the card using a card reader.

---

### Post by ki4jgt on 2010-09-25
LSUSB returns:
Bus 003 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 002: ID 03f0:2404 Hewlett-Packard (My printer)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

It doesn't even bring up f-spot. I do have batteries but it's not working and I understand that the SD card will work it's just the principal of the thing. I'm not getting my card for 5 more days, yet I have photos on my camera now. I like snapping photos of things I think are interesting. The only problem is until I get my card, I can't take any more photos.

---

