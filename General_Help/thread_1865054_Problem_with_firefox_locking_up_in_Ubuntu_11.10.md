---
title: "Problem with firefox locking up in Ubuntu 11.10"
date: 2011-10-19
forum: General Help
---

### Post by daftlad on 2011-10-19
Hi, I have done a fresh install of Ubuntu 11.10 and am having a problem with firefox and other browsers. When I open up firefox and right click on anything firefox locks up and screen goes dark. I have tried chromium and other brothers and I can right click but after a while it to crashes. 
I have tried uninstalling flash and it made no difference, have tried a different Nvid driver and no change, tried firefox in safe mode and still the same.
Current NVid driver I am using is 173
Any help would be most welcome and I sorry for any spelling mistakes as I cant right click to change the spelling...lol
My specs are


-Computer-
Processor        : AMD Athlon(tm) XP 3000+
Memory        : 1544MB (462MB used)
Operating System        : Ubuntu 11.10
User Name        : john (john)
Date/Time        : Wed 19 Oct 2011 21:12:57 BST
-Display-
Resolution        : 1280x1024 pixels
OpenGL Renderer        : GeForce 6200/AGP/SSE/3DNOW!
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : VIA8233 - VIA 8235
Audio Adapter        : MPU-401 UART - MPU-401 UART
Audio Adapter        : USB-Audio - USB Device 0x46d
-Input Devices-
 Power Button
 Power Button
 AT Translated Set 2 keyboard
 Microsoft Microsoft Notebook Optical Mouse with Tilt Wheel
 UVC Camera (046d:09a4)
-Printers-
No printers found
-SCSI Disks-
ATA WDC WD5000AAKB-0
ATA MAXTOR STM380211
ATA ST380012ACE
BENQ DVD DC DW1670
Verbatim STORE N GO

---

### Post by chubinator on 2011-10-19
I was/am having the same problem.  I noticed in my kern.log the message:

Oct 19 22:48:45 mml-desktop kernel: [ 2267.302772] 4:3:4: usb_set_interface failed 

This was repeating over and over.  Found this link:

[http://www.techytalk.info/logitech-e3500-webcam-and-cannot-set-freq-16000-to-ep-0x86/](http://www.techytalk.info/logitech-e3500-webcam-and-cannot-set-freq-16000-to-ep-0x86/)

Fixed that issue, and now my firefox seems happy.  I'll keep monitoring.  Wouldn't think they were related, but possible the sound system was causing other things to hang?

I'll keep watching mine, but worth a look on your end.

---

### Post by chubinator on 2011-10-19
I should add--I didn't follow the instructions on that link just yet--I simply unplugged my webcam for now.

---

### Post by daftlad on 2011-10-20
I have looked at my kern log file and did find the same fault as you, but unpluged web cam and still no good. I tried the script and still no joy. Thanks anyway and I will keep on trying.

---

### Post by chubinator on 2011-10-20
Sorry to hear that.  In my case, the freezes have stopped completely without the webcam plugged in.

---

### Post by paulx1 on 2011-10-23
The script worked for me, but I had to amend it to check for "cannot set freq 48000 to ep 0x86"

can test if it will work before setting up the script by running:
sudo rmmod -w snd-usb-audio
sudo modprobe snd-usb-audio

---

