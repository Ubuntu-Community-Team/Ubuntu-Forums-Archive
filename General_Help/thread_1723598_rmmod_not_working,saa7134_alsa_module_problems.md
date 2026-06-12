---
title: "rmmod not working,saa7134_alsa module problems"
date: 2011-04-07
forum: General Help
---

### Post by konsta82 on 2011-04-07
I'm trying to remove this module,but I can't. 
First of all,I'm trying to activate tv tuner card,so I started this scrip in hope I'll get correct card number.
```
#/bin/sh
MAXTUNER=69
i=0

while [ $i -lt $MAXTUNER ];
do
  rmmod saa7134_alsa saa7134
  modprobe saa7134 card=$i
  echo "Actual card is:" $i
  sleep 1 # this is to make sure /dev/video is registered when tvtime starts
  tvtime
  i=$(($i+1))
done
```

Also,tried to manually remove this module with rmmod,but it didn't worked.

```
konsta@konsta:~$ sudo rmmod saa7134-alsa
[sudo] password for konsta:
ERROR: Module saa7134_alsa is in use
konsta@konsta:~$ sudo rmmod konsta@konsta:~$ sudo rmmod saa7134-alsa
[sudo] password for konsta:
ERROR: Module saa7134_alsa is in use
konsta@konsta:~$ sudo rmmod saa7134
ERROR: Module saa7134 is in use by saa7134_alsa
``` 
As I understand,it is necessary to remove old module before testing new one.
What to do,how to get rid of saa7134_alsa ?
Is there alternative way to find tuner settings ?

---

### Post by konsta82 on 2011-04-07
Situation is like in this thread,still without solution

[http://ubuntuforums.org/showthread.php?t=408654]("http://ubuntuforums.org/showthread.php?t=408654")

they are now blacklisted,but no changes

> # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist saa7134_alsa
blacklist saa7134

---

