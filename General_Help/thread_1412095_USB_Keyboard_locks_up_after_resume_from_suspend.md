---
title: "USB Keyboard locks up after resume from suspend"
date: 2010-02-20
forum: General Help
---

### Post by alienexplorers on 2010-02-20
I am hoping that someone can give me a bit of help.  When I suspend my computer and then resume later in the day my USB keyboard locks up.  The only way I have found to reset the keyboard is to disconnect the USB cable from the USB port and then reconnect it.  If anyone knows an easier way to fix this problem I would like to hear from you.

Thanks
Donnie

---

### Post by alienexplorers on 2010-02-21
Bump

---

### Post by bleedingpowers on 2011-06-12
I'm facing a similar situation after suspend. The computer wakes up but neither my usb mouse nor keyboard work on resume. The input devices work again if I restart the computer. I tried modifying some grub options but no luck.

Any pointers are extremely welcome...Every time I updgrade Ubuntu something breaks....WTF?

---

### Post by walt.smith1960 on 2011-06-12
I can't provide specific help, sorry.  I had a USB WiFi adapter behaving exactly the same, would not wake up after suspending.  The problem was that the device was not disconnected before the machine itself suspended.  Apparently USB devices need to be disconnected prior to suspend then reconnected once the machine unsuspends.  Here is a link to the thread. [http://ubuntuforums.org/showthread.php?t=1745769&highlight=suspend](http://ubuntuforums.org/showthread.php?t=1745769&highlight=suspend).  You'd have to figure out which module is used for the keyboard/mouse and modify the code as required.  There's no guarantee this solution would fix your problem but it did fix mine. HTH.

---

### Post by bleedingpowers on 2011-06-18
Although Walt's advice seems to point in a right direction, making changes in the /etc/pm/config.d/config file did not have any effect.

Now, I realized that this problem is more weird than I thought: it is only the usb ports on one side that stop working for hid's (mouse, keyboard), the ports remain alive for usb storage devices. I don't understand, the other side's USB port behaves correctly.

Also, I was able to add the "wacom" module to the **MODULES** list in the acpi-support file. ```
sudo vim /etc/default/acpi-support
```
This works for the touch-screen after resuming from sleep:
```
MODULES="wacom"
```

However, when I add the "hid" or "usbhid" modules there, everything breaks and not even the touch-screen's wacom module survives. For example, this doesn't work:
```
MODULES="wacom hid"
```

I'm still hoping somebody can point me to the right solution...

---

### Post by bleedingpowers on 2011-06-28
I realized that the problem seems to be more like a power issue since (according to the *pm-suspend.log*) modules (such as wacom, usb_hid) unload and reload properly after suspend/resume-from-suspend. 

There's got to be another reason for this to be happening. The usb modules (usb_hid, usb_storage) seem to work, but the usb hub appears to become disabled for powering the keyboard or the touch-screen (I don't know the exact internal architecture of my HP TouchSmart tm2).

Did anyone find a solution yet?

---

### Post by cefn on 2011-07-03
I'm experiencing a similar issue now even without going through a suspend/resume cycle (originally it only happened on suspend/resume). 

I find that as long as I keep sending events over a keyboard or mouse (move the trackball, or hit keys) then they stay connected. However, if I stop, then they lose connection.

As a workaround I've found that running lsusb from the console seems to cause them to wake up again without a reboot. However, for me that only lasts for about 10 seconds unless I keep using them continuously.

The inbuilt keyboard and trackpad on the laptop continue working throughout - it's just the USB devices which die.

One weird thing is that my USB tether to my phone (which gives me network) carries on going all the time, so the USB subsystem must remain functional throughout.

I've filed a bug against xserver-xorg-input-evdev in case there's anyone there who can help. If you have the same problem, then track that bug. However, if your symptoms are (even slightly) different, then I suggest filing a different bug.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/800110](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/800110)

---

### Post by bleedingpowers on 2011-07-03
I'm curious...do you lose power on the external keyboard when it stops working? Do the keyboard's LEDs stay on? Mine dies completely...and it's backlit, so no light (power) seems to be delivered from this particular hub to the device. However, this doesn't happen on the usb hub on the other side of the laptop...weird!

---

### Post by eriksnow on 2011-07-03
Hey guys, I have a tm2-2050ca and have yet to replicate this problem. The closest thing I've seen is my mouse occasionally does not click or register clicks after resuming from sleep. I can move it around but the clicker or tapping on it does not actually work. Other issues could be the Wifi, but I've noticed on any laptop with Linux it takes about 10 seconds after waking up to register and activate wireless, and then it works fine. I'm running 10.10 right now, holding off on the 11.04 release until others have tested but... what the heck, I'll throw it on there sometime over the next couple days and see if I have issues with resuming from suspend.

---

### Post by bleedingpowers on 2011-07-03
> **eriksnow said:**
> Hey guys, I have a tm2-2050ca and have yet to replicate this problem. The closest thing I've seen is my mouse occasionally does not click or register clicks after resuming from sleep. I can move it around but the clicker or tapping on it does not actually work. Other issues could be the Wifi, but I've noticed on any laptop with Linux it takes about 10 seconds after waking up to register and activate wireless, and then it works fine. I'm running 10.10 right now, holding off on the 11.04 release until others have tested but... what the heck, I'll throw it on there sometime over the next couple days and see if I have issues with resuming from suspend.

The problem I'm experiencing all started just after the upgrade to Natty (Ubuntu 11.04)...everything was okay before. If you want to save the headaches, don't upgrade just yet...IMHO

---

