---
title: "Soundcard not detected and strange USB device behaviour after jaunty update"
date: 2009-10-03
forum: General Help
---

### Post by gowron on 2009-10-03
Hello, this morning I updated my Ubuntu installation as suggested by the update manager utility. I've attached the term.log file concerning this update (there was a kernel update).
After the update Ubuntu asked for a reboot and I did it. 
During the boot sequence, when Ubuntu tried to start the bluetooth service, it seemed to check without success any usb device attached to the PC (a wireless USB keyboard+mouse and a WiFi device) to see if it was a bluetooth device. The system continued to return error messages but then it started almost normally. Almost because I wasn't able to use the WiFi USB device, I had to unplug it and change the USB port, then it started. I disabled the bluetooth service to solve the issue. After a second boot, I had also to unplug and change the port of the keyboard along with that of the WiFi device to make them work. 
Then I noticed that there was no audio. In fact Ubuntu isn't able to detect my soundcard anymore. aplay -l says that no audio device is detected, however lspci lists the soundcard.

My configuration is the following one:

Motherboard: Asus P5Q-EM with onboard soundcard Realtek ALC1200
Videocard: Nvidia Gainward 9400 GT

Nvidia driver 185.18.36
ALSA driver 1.0.21 

Any suggestion? I'm almost new to Linux.

Thanks in advance.

---

### Post by DFlame on 2009-10-03
As there was a kernel update, let's begin by trying the previous kernel to see if that resolves the issue first.

Restart the computer, and hit Esc when prompted to show the GRUB boot menu. You should have 4 (or more) entries with the latest version at the top and the older versions working towards the bottom. Each version may have a recovery mode too.

Pick your previous kernel (should be the 3rd one down on a 'regular' system) and hit Enter to boot it. Use a regular, non-recovery kernel for now.

When the system boots with this older version, does the problem persist?

---

### Post by gowron on 2009-10-03
> **DFlame said:**
> As there was a kernel update, let's begin by trying the previous kernel to see if that resolves the issue first.

Restart the computer, and hit Esc when prompted to show the GRUB boot menu. You should have 4 (or more) entries with the latest version at the top and the older versions working towards the bottom. Each version may have a recovery mode too.

Pick your previous kernel (should be the 3rd one down on a 'regular' system) and hit Enter to boot it. Use a regular, non-recovery kernel for now.

When the system boots with this older version, does the problem persist?

Just tried. Audio came back, but USB devices behaviour did not change.

This time during boot the system returned some messages like this one 
```
usb 2-2: device descriptor read/64, error -110
```

---

### Post by DFlame on 2009-10-03
Well we're halfway there :) While you're in the older kernel, revert any configuration changes you've made to attempt to resolve the problem if you can, then restart the computer with your regular devices plugged in.

If it works, good. If it doesn't, remove the USB device and use an alternate port again to get it working. Afterwards, open a Terminal window and enter the following command:

```
gedit /var/log/dmesg
```

The text editor will show a fairly large log. Instead of posting it here, upload it to [Pastebin](http://www.pastebin.com) and link to it here so we can take a further look.

---

### Post by gowron on 2009-10-04
> **DFlame said:**
> Well we're halfway there :) While you're in the older kernel, revert any configuration changes you've made to attempt to resolve the problem if you can, then restart the computer with your regular devices plugged in.

Thanks for the help.
How am I supposed to revert back to the previous configuration? Have I to force the use of the previous version for the updated packets, only for the kernel-related ones? 
I'm trying to figure out which packet could cause such a strange behaviour without success.

EDIT: I recompiled the alsa packets (I have manually installed version 1.0.21 to get audio over HDMI working) and now I have audio also with the new kernel. I've also plugged a standard PS2 keyboard and an USB mouse instead of the wireless keyboard&mouse (that is a recent bought) to see if the problem has been caused by it. Well, obviously the keyboard did not cause any problem while the mouse remain undetected until unplugged and replugged. I've also noticed that sometimes (I think mainly after a cold boot) everything works fine (dmesg does not contain any error messages).

Here the dmesg log related to a warm boot with my wireless mouse&keyboard and my wifi device plugged [http://pastebin.com/f6b5a411b](http://pastebin.com/f6b5a411b)

---

### Post by gowron on 2009-10-05
I've found this thread about a similar problem
[http://ubuntuforums.org/showthread.php?t=1004516](http://ubuntuforums.org/showthread.php?t=1004516)

but no solution...

---

### Post by koma77 on 2009-10-05
I just ran into this problem as well.
At the moment I suspect that there might be a problem with my USB hub...
I get:

```
device descriptor read/64, error -110
```

when I boot and also when I plug devices into (at least) the hub.

---

### Post by koma77 on 2009-10-05
I also noted that running lsusb takes forever... Is that the same for you?

---

### Post by koma77 on 2009-10-05
Ok, after some more testing I found that my wireless network device did not show up in the network manager.

It is an on-board USB wifi-adapter on my ASUS motherboard.

I disabled it in BIOS and now everything works (but of course not the wireless network).

I verified by booting XP. The wireless device was gone there as well. I guess it actually broke and pested the USB bus! Darn it.

---

### Post by gowron on 2009-10-06
> **koma77 said:**
> I also noted that running lsusb takes forever... Is that the same for you?

No, I have no problem with lsusb. I just have to unplug e replug all usb devices after a warm boot to get them recognized. I think I'm going to install windows too to check if it is an hardware problem (but I don't think so).

---

