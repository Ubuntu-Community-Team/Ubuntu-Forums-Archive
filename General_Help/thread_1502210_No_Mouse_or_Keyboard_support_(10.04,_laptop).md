---
title: "No Mouse or Keyboard support (10.04, laptop)"
date: 2010-06-05
forum: General Help
---

### Post by WutCake on 2010-06-05
title says it all,

using U10.04, i upgraded from 9.04, now keyboard or mouse wont work.

using a laptop, ect ect, dont really know what kind of info you need to know how to help me..

---

### Post by jesuisbenjamin on 2010-06-05
Did you try to re-boot? I have the same problem from time to time on my laptop, but rebooting somehow helps (sometimes after several reboot).
See thread [http://ubuntuforums.org/showthread.php?t=1381831](http://ubuntuforums.org/showthread.php?t=1381831)
if you feel it is the same topic.

I have no better answer unfortunately.

---

### Post by WutCake on 2010-06-05
> **jesuisbenjamin said:**
> Did you try to re-boot? I have the same problem from time to time on my laptop, but rebooting somehow helps (sometimes after several reboot).
See thread [http://ubuntuforums.org/showthread.php?t=1381831](http://ubuntuforums.org/showthread.php?t=1381831)
if you feel it is the same topic.

I have no better answer unfortunately.

well, yeah, it works before you actually end up in the OS, but i haven't encountered that it works with rebooting multiply times.

edit: i use laptopkeyboard + touchpad and/or usbmouse, none of them are working. i have no problem with login, as i'm auto-login.

---

### Post by xbush on 2010-06-06
I just upgraded as well and lost my keyboard and mouse.  It's a Logitech Bluetooth desktop set.  I had to click on the Bluetooth icon in the tray and open the properties page to add the devices.  The mouse and keyboard were found, connected, and set up in minutes.  If your tray does not show the BT icon then System, Preferences, Bluetooth.
  If your keyboard/mouse is not Bluetooth then you have a different problem and hopefully someone else will reply to help you.

Good Luck!

---

### Post by WutCake on 2010-06-06
> **xbush said:**
> I just upgraded as well and lost my keyboard and mouse.  It's a Logitech Bluetooth desktop set.  I had to click on the Bluetooth icon in the tray and open the properties page to add the devices.  The mouse and keyboard were found, connected, and set up in minutes.  If your tray does not show the BT icon then System, Preferences, Bluetooth.
  If your keyboard/mouse is not Bluetooth then you have a different problem and hopefully someone else will reply to help you.

Good Luck!

did you even read the thread?
no im not using bluetooth mouse/keyboard.
:(

sometimes i really with i had a bluetooh mouse/keyboard haha.

---

### Post by WutCake on 2010-06-10
Bump because i NEED help!

---

### Post by NoranaC on 2010-06-13
I am having the same problem.  I just upgraded from 9.04 to 10.04 and have no keyboard (a regular old USB device) or mouse support (a wireless USB mouse).  I can use my keyboard before I make it to the ubuntu OS.

---

### Post by WutCake on 2010-06-14
anyone, please...
even if you dont know how to fix it, give us other stuffs that might be a part of the problem :(

---

### Post by TopEnder on 2010-06-15
Just a small point, have you checked your CMOS settings?  In my CMOS settings under Integrated Peripherals there are four entries for USB, 2 for USB 1.1/2.0 Controller, one for USB Keyboard Support and one for USB Mouse Support, if I do not have these enabled I can not use the keyboard or mouse.  If I set the BIOS up to boot Win XP Pro with out the enabled USB Keyboard/Mouse Support, Windows will boot and I can use the USB Keyboard/Mouse, where when setting the BIOS to boot Ubuntu without the USB Keyboard/Mouse enabled both will not work, it appears Ubuntu  boots to what the CMOS fields are set to which is good).  Hope this is of some help to you.

---

### Post by WutCake on 2010-06-16
> **TopEnder said:**
> Just a small point, have you checked your CMOS settings?  In my CMOS settings under Integrated Peripherals there are four entries for USB, 2 for USB 1.1/2.0 Controller, one for USB Keyboard Support and one for USB Mouse Support, if I do not have these enabled I can not use the keyboard or mouse.  If I set the BIOS up to boot Win XP Pro with out the enabled USB Keyboard/Mouse Support, Windows will boot and I can use the USB Keyboard/Mouse, where when setting the BIOS to boot Ubuntu without the USB Keyboard/Mouse enabled both will not work, it appears Ubuntu  boots to what the CMOS fields are set to which is good).  Hope this is of some help to you.

im not sure what you mean with CMOS, but keyboard/mouse was/is working on any other OS i have(the was part is U9.04).

where is this "CMOS"?

---

### Post by TopEnder on 2010-06-21
WutCAke, Sorry for the delay, been busy showing the Southerners around the Top End.  The CMOS setting are part of  the BIOS setting for the Motherboard, ( mine is a Gigabyte S-Series).

---

### Post by WutCake on 2010-06-24
> **TopEnder said:**
> WutCAke, Sorry for the delay, been busy showing the Southerners around the Top End.  The CMOS setting are part of  the BIOS setting for the Motherboard, ( mine is a Gigabyte S-Series).

oh ok.

i didn't find anything in my Bios about mouse or keyboard, but then again, mouse & keyboard works fine in liveCD, and windows.

my bios is "Phoenix Bios" but i think its more of a driver issue.

---

### Post by WutCake on 2010-06-26
oh man, i feel so silly now.

when i reformated windows and as you might or might not know, windows takes over the boot settings, so i had to reinstall Grub, since i got Ubuntu 10.04 now and it uses Grub2, i thought it would be a good idea to install it with Grub2 too.

and so i did, after some googling how to do so (didnt seem like it was just doing "grub" in terminal with a livecd! ) i got it working and so on, i reboot into ubuntu just to check that everything worked with grub, and suddenly mouse and keyboard worked!

so, it seems like the Legacy Grub was caused the problem.

Edit: why did it generate a menu.lst file? i thought Grub2 wouldnt use such file o.o

---

### Post by ajay_g_m on 2010-07-04
I have a similar issue after upgrade from 9.04 to 10.04. 
My mouse works till the first login screen. After login the mouse icon disappears, but if I move the mouse I can see that the desktop icons get the focus and loose focus successfully, but the mouse icon is not visible. 
I seem to be having a workaround. If I lock the desktop (using CTL+ALT+L) and then move the mouse then I can see the mouse icon and the mouse stays functional thenceforth. 
I hope the above workaround helps.

---

### Post by RS232C on 2010-07-08
That is not the problem I am having and I suspect others as well. with me, I'll be usually online, and my USB mouse will just freeze, and it's light will go off (I have a laser mouse on this system.) I can restore the state of my system by cntrl-alt-del and choosing hybernate, which saves on the hd then boots up in exactly the same, and I suspect it doesn;t save the USB drivers, but rather reloads them fresh thus is why it works when it comes back, but then it will go out again eventually. I'm using a logitech wheel mouse, but seriously do not think that has anything to do with it. also when I hit hybernation, it gives me errors before saving the system state, like usb cannot read/write # to device error -110 or such. the # changes the error doesn't. keyboard works perfectly fine, and it is not a usb keyboard, but the mouse dies. This is a pretty serious problem...and very annoying. I use slax and various other os's and nothing like this happens with them ever, so I'm guessing it's a ubunto problem. 10.04 btw.amd 2400+ system.

---

