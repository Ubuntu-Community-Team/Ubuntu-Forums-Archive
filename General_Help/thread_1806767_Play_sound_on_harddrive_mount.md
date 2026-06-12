---
title: "Play sound on harddrive mount?"
date: 2011-07-18
forum: General Help
---

### Post by pbeesley on 2011-07-18
Hey guys, just wondering if its possible to have unbuntu play a sound when I mount a harddrive...

for example if I mounted the harddrive...lets call it "Superstar" it would play an mp3 file recording of a computer voice saying "superstar now mounted"

is this possible?

Thanks :KS

---

### Post by Grenage on 2011-07-18
It is! That's the good news; the bad news is that it's not something you can configure in the GUI.

You basically need to create a udev rule which either runs the command to play a sound (or a script which will play a sound) when a device is connected.  You can have the rule play the same sound for each device, or a separate sound for each device.

For example, plug in your USB drive and type this:

```
lsusb
```

You'll get output such as:
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 005 Device 005: ID 0204:6025 Chipsbank Microelectronics Co., Ltd CBM2080 Flash drive controller**
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04f3:0210 Elan Microelectronics Corp. AM-400 Hama Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
I've highlighted the drive I'm interested in.

The two bits of info I'm interested in are the vendor and product IDs, listed respectively as 0204 and 6025.

Now we need to edit a file to add the rule:

```
gksu gedit /etc/udev/rules.d/10-local.rules
```

Here's an example of a rule I might add:

```
ACTION=="add", ATTRS{idVendor}=="0204", ATTRS{idProduct}=="6025", RUN+="/home/grenage/superscript.sh"
```

You could replace the script with a command to play an MP3, or just put the command inside a script.  The udev rules simply filter the input, so I *think* that if you wanted this to apply to _all_ drives when they get plugged in, you can simply remove the vendor and product sections.

---

### Post by pbeesley on 2011-07-18
perfect thanks, I'll give this a go :D
:KS

---

### Post by Grenage on 2011-07-18
Top stuff.  I should have added that the udev rule will run the command just *before* the actual mount takes place, so you'll need to factor that in if you do anything that accesses the drive itself.

---

