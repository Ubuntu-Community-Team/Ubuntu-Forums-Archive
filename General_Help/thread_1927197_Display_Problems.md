---
title: "Display Problems"
date: 2012-02-17
forum: General Help
---

### Post by caned_monkey on 2012-02-17
Hello,

I've got a problem with my display, when I maximise a window it sits too high on the screen and i have to drag it down and, when the launcher is on autohide, it dosen't matter how close i put the mouse cursor to the edge of the screen it wont reappear. Its like the screen isn't aligned properly.

Let me know if you need any more info.

Thanks in advance

---

### Post by caned_monkey on 2012-02-18
Bump :D

---

### Post by cogier on 2012-02-18
Your profile does not say which version of Ubuntu you are using.

Please don't take this as a telling off, it's just that people will need more details so that they can help you. This is especially relevant when you could be using Gnome2,  Unity, KDE ....

---

### Post by Leppie on 2012-02-18
> **caned_monkey said:**
> Its like the screen isn't aligned properly.
Have you tried calibrating your monitor? Usually it has a button for this, or you can find this option in the monitor's menu.

---

### Post by caned_monkey on 2012-02-18
> **cogier said:**
> Your profile does not say which version of Ubuntu you are using.

Please don't take this as a telling off, it's just that people will need more details so that they can help you. This is especially relevant when you could be using Gnome2,  Unity, KDE ....

I cannot edit my profile until I've made 50 posts but sorry, i was assuming you were all psychic ;-)

I'm using Ubunbtu 11.10

---

### Post by caned_monkey on 2012-02-18
> **Leppie said:**
> Have you tried calibrating your monitor? Usually it has a button for this, or you can find this option in the monitor's menu.

I've tried that and also did a factory reset but it didn't help. it's weird because the menu bar at the top sits in the right position and the launcher dosent sit too low on the screen. I should also mention that i have moved the launcher to the bottom of the screen.

---

### Post by Leppie on 2012-02-18
could you post the output of the following commands:
```
lshw -c video
lsmod | grep video
```

---

### Post by caned_monkey on 2012-02-18
WARNING: you should run this program as super-user.
  *-display:0             
       description: VGA compatible controller
       product: 82G965 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:dfe00000-dfefffff memory:c0000000-cfffffff ioport:ec98(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82G965 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:dff00000-dfffffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
smsc@Number1:~$ lsmod | grep video
video                  18908  1 i915

---

### Post by Leppie on 2012-02-18
could you post your /etc/modprobe.d/blacklist.conf and the output of the following command:
```
ls -al /etc/modprobe.d/
```

---

### Post by caned_monkey on 2012-02-18
total 52
drwxr-xr-x   2 root root  4096 2012-02-05 13:20 .
drwxr-xr-x 137 root root 12288 2012-02-18 20:05 ..
-rw-r--r--   1 root root  2507 2011-05-05 06:26 alsa-base.conf
-rw-r--r--   1 root root   325 2011-06-15 17:57 blacklist-ath_pci.conf
-rw-r--r--   1 root root  1603 2011-06-15 17:57 blacklist.conf
-rw-r--r--   1 root root   108 2011-09-27 13:47 blacklist-cups-usblp.conf
-rw-r--r--   1 root root   210 2011-06-15 17:57 blacklist-firewire.conf
-rw-r--r--   1 root root   661 2011-06-15 17:57 blacklist-framebuffer.conf
-rw-r--r--   1 root root   156 2011-05-05 06:26 blacklist-modem.conf
lrwxrwxrwx   1 root root    41 2012-02-05 11:44 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root   583 2011-06-15 17:57 blacklist-rare-network.conf
-rw-r--r--   1 root root  1077 2011-06-15 17:57 blacklist-watchdog.conf

When I enter /etc/modprobe.d/blacklist.conf, I get:

bash: /etc/modprobe.d/blacklist.conf: Permission denied

---

### Post by Leppie on 2012-02-18
> **caned_monkey said:**
> 
When I enter /etc/modprobe.d/blacklist.conf, I get:

bash: /etc/modprobe.d/blacklist.conf: Permission denied
try this:
```
cat /etc/modprobe.d/blacklist.conf
```

---

### Post by caned_monkey on 2012-02-18
That worked:

# This file lists those modules which we don't want to be loaded by
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

---

### Post by Leppie on 2012-02-18
> **caned_monkey said:**
> 
smsc@Number1:~$ lsmod | grep video
video                  18908  1 i915
Is this really all the output you got from that?
It should like like this:
```
lsmod | grep video
uvcvideo               57559  0 
videodev               70686  1 uvcvideo
media                  18148  2 uvcvideo,videodev
v4l2_compat_ioctl32    16663  1 videodev
i2c_core               23766  6 videodev,i915,drm_kms_helper,drm,i2c_algo_bit,i2c_i801
video                  17553  1 i915
usbcore               127444  6 uvcvideo,usb_storage,usbhid,uas,ehci_hcd
thermal_sys            17992  3 video,processor,thermal
 
```

Have you ever noticed any errors during boot? Or do you have the normal animated boot screen?

---

### Post by caned_monkey on 2012-02-19
I tried it again and this is all I get:

smsc@Number1:~$ lsmod | grep video
video                  18908  1 i915

I've never noticed anything unusual during boot, everything looks normal. Another thing I have noticed is, when i maximize a window and it sits too far up in the screen you cant click anything or highlight any text in the window as the cursor keeps missing the target... if that makes sense?

---

