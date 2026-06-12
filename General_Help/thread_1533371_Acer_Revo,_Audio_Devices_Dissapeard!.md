---
title: "Acer Revo, Audio Devices Dissapeard!"
date: 2010-07-17
forum: General Help
---

### Post by niietzshe on 2010-07-17
Hey everyone,
I've just been setting up my new Revo with Ubuntu for use as a HTPC with XBMC etc..
Previously I had audio coming out through HDMI, but now I have lost all devices under the sound settings.

I was using alsa mixer, is there any way of getting this working again? A HTPC without sound is a bit useless!

I can't really say what I've done, as I took a few approaches to it, but I've tried to remove everything so it's back to normal. I think maybe it happened after updating some NVIDIA drivers...

Any ideas?
Niietzshe

---

### Post by niietzshe on 2010-07-17
Ok so XBMC is quitting as soon as I try to run a MKV which should use the VDPAU drivers. So I'm starting to think this is a NVIDIA thing.

---

### Post by lidex on 2010-07-18
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#*
sudo lshw -C display 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by niietzshe on 2010-07-18
Thanks for responding!

```
uname -a
Linux HTPC 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux
``````
aplay -l
**** List of PLAYBACK Hardware Devices ****
ALSA lib conf.c:1645:(snd_config_load1) _toplevel_:234:69:Unexpected char
ALSA lib conf.c:3425:(snd_config_hook_load) /home/chris/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:3286:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3671:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:232: control open (0): Invalid argument

```Looks like I've messed up the .asoundrc there!

```
dpkg -l | grep "alsa"
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA
``````
head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC662 rev1

==> /proc/asound/card0/codec#3 <==
Codec: Nvidia MCP7A HDMI
``````
sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: ION VGA
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: b1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:21 memory:fb000000-fbffffff memory:e0000000-efffffff(prefetchable) memory:f8000000-f9ffffff(prefetchable) ioport:ec00(size=128) memory:fafe0000-faffffff(prefetchable)
```

The computer is an[ Acer Aspire Revo R3610]("http://www.acer.co.uk/acer/productv.do?LanguageISOCtxParam=en&kcond61e.c2att101=68913&sp=page16e&ctx2.c2att1=17&link=ln438e&CountryISOCtxParam=UK&ctx1g.c2att92=242&ctx1.att21k=1&CRC=2669969291")

Hope that helps to clarify what's going on here.
Thanks
Niietzshe

---

### Post by lidex on 2010-07-18
Yeah, fix or remove .asoundrc. Next I would suggest upgrading alsa via the alsa-upgrade link in my sig.

---

### Post by niietzshe on 2010-07-19
Thanks for that, I removed the file and it worked fine.
Once I have a few other things sorted I'm going to upgrade the alsa drivers and start testing 5.1 etc...

Thanks a lot!
Niietzshe

---

### Post by lidex on 2010-07-19
Good stuff. Would you please mark the thread as solved when you get a chance?

---

