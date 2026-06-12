---
title: "Wireless USB Mouse Randomly Quits Working"
date: 2006-06-17
forum: General Help
---

### Post by captain_bogus on 2006-06-17
Hi, every 2 to 20 minutes my wireless USB mouse just quits working.  No motion, no button clicks, nothing.  It's a Kensington pocket mouse, the USB plugin looks like a pen drive and has a red light that blinks when I move the mouse.  The light will continue to blink when it freezes up and I move the mouse so I don't think it's a hardware problem.  Plus, in windows, this never happens.  And no, it's not the batteries:p .

I'm using a Toshiba Satellite L25 with a touchpad so when my mouse freezes up I can start using my touchpad, thankfully.

The only thing that's works is rebooting.

I've tried unplugging the little pen drive looking thing and replugging it, that doesn't work.  Nor does plugging it in a different USB port.

I've also tried a couple of solutions I found here:
[http://www.ubuntuforums.org/showthread.php?t=127027&highlight=usb+mouse+quit+working](http://www.ubuntuforums.org/showthread.php?t=127027&highlight=usb+mouse+quit+working)
They don't work either.  

Output of lsusb
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 047d:1035 Kensington
Bus 002 Device 001: ID 0000:0000

Output of dmesg | grep usb
[17179578.008000] usbcore: registered new driver usbfs
[17179578.008000] usbcore: registered new driver hub
[17179579.828000] usb 2-4: new low speed USB device using ohci_hcd and address 2
[17179580.048000] usbcore: registered new driver hiddev
[17179580.060000] input: USB HID v1.10 Mouse [Kensington Kensington USB Mouse] o n usb-0000:00:13.1-4
[17179580.060000] usbcore: registered new driver usbhid
[17179580.060000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver

Any ideas?

--bog

---

### Post by captain_bogus on 2006-06-24
Please?

---

### Post by captain_bogus on 2006-07-04
Did I post this in the wrong forum?

--bog

---

### Post by jimmygoon on 2006-07-04
try it on another computer. my bet is, is that its broken. I had the same problem with one of my mouses.

---

### Post by kb2wdi on 2006-07-04
The next time it freezes, try un-plugging and re-plugging the USB adapter.
I have a MS Optical (not wireless) mouse that this happens to when connected to USB. It works fine with the PS/2 adapter though. My USB bluetooth adapter also drops out from time to time. The issue may be with the USB chipset and driver.

---

### Post by chipmonk010 on 2006-07-04
this is a weird problem with the ati-accelerated graphics driver and usb. Quick fix is to do this:

sudo gedit /etc/X11/xorg.conf
goto the Devices section and change the driver from fglrx to ati

OR do:

sudo dpkg-reconfigure xserver-xorg
when asked which driver to use pick ati instead of fglrx

i have the same laptop(L24) and the same problem. The above solution solves it but i have no graphics acceleration. Im trying to find the other thread on this right now to see if there is a solution yet.

Chris

EDIT:
heres one of the threads but no solution *WITH 3D Acell. enabled*
maybe the drivers from ati's website would work better?
[http://www.ubuntuforums.org/showthread.php?t=189572&highlight=usb+mouse](http://www.ubuntuforums.org/showthread.php?t=189572&highlight=usb+mouse)

---

### Post by captain_bogus on 2006-07-06
Thank you everyone.

The mouse isn't broken.  I've been using *cough* windows for the past 2 weeks and the mouse never turns off under that OS.  (I have dual-boot.)

Unplugging it and replugging it does nothing.  Even plugging it into a different USB port.

Chipmunk, I'm using ATI's drivers from their website.  I guess I gotta go and reconfig X to use the generic ATI driver.

Thanks for the tip.  I guess we gotta decide if we want accelerated graphics or a USB mouse, lol.  Can't have both:-D !

--bog

Edit:  Switching to the generic ati drivers and re-starting X worked.  Mouse no longer stops working.  Thanks Chipmunk.

---

### Post by chipmonk010 on 2006-07-10
no problem captain, it sucks u have to pick one or the other but its better then nothin...FYI this problem is not ubuntu's fault, it lies somewhere in the closed-source drivers writen by ati. 

Something you might wanna try is a program called 'synergy' if you have your laptop on your desk next to your desktop. Its in apt and the just google synergy and the first site is the developers home page.
    This progy basically lets you slide your mouse pointer off the edge of your desktops screen and onto your laptop, thereby sharing your mouse and keyboard via a network connection. I find it to be quite useful and it iliminated the usb mouse! I havent tried it with anything but the generic ATI driver but its worth a shot and a nice this to mess with.

later
Chris

EDIT: synergy will work on windows pcs and a combo windows:desktop linux:laptop also

---

