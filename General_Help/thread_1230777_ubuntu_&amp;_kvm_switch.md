---
title: "ubuntu &amp; kvm switch"
date: 2009-08-03
forum: General Help
---

### Post by trubliphone on 2009-08-03
Hello.

I have a Dell 1318 Inspiron laptop.  I have recently installed Kubuntu 9.04 (dual-boot with Vista).  I am very happy with it.  We also have an ancient desktop (WinXP) with a 20" LCD monitor.  Usually, other people are using the desktop.  For those times that they aren't, though, I've bought a KVM switch to let me use the bigger monitor & keyboard.

The KVM switch is a TrendNet TK-205 2-port PS/22 KVM switch.  (I tried the USB version, but it wouldn't work with my setup).  As the laptop has no PS/22 inputs, I bought a USB to PS/2 adapter which lets 2 PS/2 devices use a single USB switch.

If I boot up the laptop with the KVM switch connected, then the monitor works fine.  I find that I have to connect the PS/2 inputs to the USB to PS/2 adapter one at a time in order to get the mouse & keyboard to work - I can live with this.  And I can use the buttons on the switch to swap between the desktop and laptop.  So far so good.

But there are two annoyances:

1) Why do I have to reboot my laptop in order for it to recognize the switch?  I would like to be able to just plug in the switch while the laptop is running and have it automatically recognized.

2) When I switch from using the big monitor to the laptop's monitor, I find that the display settings have altered; it is only using a fraction of the display space.  I can get around this by rebooting; but like I mentioned earlier, I'd much prefer just resetting it on-the-fly.  Does anybody know how to do this?

Thank you for your help.

---

### Post by HuckleSmothered on 2009-08-04
And here I sit having just resolved a major KVM issue myself. Mine was with RedHat Enterprise, however. The problem was with the resolution, which sounds like is one of your complaints. 

First complaint of having to restart, you might be able to get away with restarting X Windows. Which is done with logging out and logging back in. Change displays and hardware and X Windows won't know about it until it gets restarted itself. No reason for X Windows to assume it needs to check monitors except on start up.

Second complaint, not using full display potential. My specific problem was with the KVM not passing along the proper monitor information and giving my linux box a basic monitor profile, which only supported 1024x768 (I wanted 1280x1024). Turned out that the information is passed in something called DDC. I put in a line in my Device (I think) subsection in my xorg.conf file that read something like this (not specific, you should research it to find it specifically):
Option    "NoDDC"  "true"
Might also want to research an option for EDID or EDIC also. I never needed to go that far as the NoDDC worked just fine for me. This will prevent the KVM from overriding your xorg.conf file with its generic stuff.

---

### Post by dcstar on 2009-08-05
> **trubliphone said:**
> 
..........
2) When I switch from using the big monitor to the laptop's monitor, I find that the display settings have altered; it is only using a fraction of the display space.  I can get around this by rebooting; but like I mentioned earlier, I'd much prefer just resetting it on-the-fly.  Does anybody know how to do this?


The following command (run in the CTRL-ALT-F1 screen) will restart the X system without a reboot - but it will log you out:

```
sudo /etc/init.d/gdm restart
```

There may well be a less drastic command to have the display stuff reset (like when laptops switch to external and back), but I don't know of it.

---

### Post by trubliphone on 2009-08-08
Thank you for the advice.  I can deal with the resolution by logging out and back in.

However, I am now having more problems; the KVM switch (or, specifically, I think, the PS/2 to USB adapter that connects the mouse and keyboard from the KVM switch to the USB port in my laptop) doesn't seem to be recognized. 

When I boot up I get the following sorts of messages:

[33.668062] USB 5-1: device descriptor read/64, error -110
[some other number] USB 5-1: device descriptor read/64, error -110
[some other number] USB 5-1: device descriptor read/64, error -110
[some other number] USB 5-1: device descriptor read/64, error -110
[some other number] device not accepting address 4, error -110

The monitor works but the mouse and keyboard do not.  Initially this happened about 3/4 of the time; now it seems to happen all of the time.

I am running Kubuntu 9.04.  The KVM switch is a TrendNet TK-205.  The mouse and keyboard is a Logitech Cordless Desktop.  And the PS/2 to USB adapter is just some generic adapter (I don't know the model name; it says "PPA" on it).

Any advice?

---

### Post by oldsoundguy on 2009-08-08
NOT a laptop user, but DO use KVM switches.

In order to get the proper resolution(s) you have to boot in the open.  Boot each computer individually and don't switch to the other WHILE booting is in progress.  The OS has to see the display in order to activate the card settings.

---

