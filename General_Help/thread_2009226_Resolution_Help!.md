---
title: "Resolution Help!"
date: 2012-06-24
forum: General Help
---

### Post by GingerEskimo on 2012-06-24
Having issues with resolution on ubuntu 12_04LTS. 

The maximum resolution i can get is 1024x768, whereas on windows7 i have 1280x768. I've tried adding creating and editing xorg.conf, but Xorg -configure gives me the error:
```
Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log

```

So i can't add it to that.

I've tried adding it through Xrandr, but it's very difficult, using the command xrandr i get:
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        60.0  

```

I'm unsure how to add 1280x768, any help would be appreciated, cheers! :)
 - WIll

---

### Post by carl4926 on 2012-06-24
```
sudo apt-get install hwinfo
```

then:

```
sudo hwinfo --framebuffer
```

Post result

xorg.conf is history, you shouldn't need it
I'd try deleting it

You could tell us about your hardware though

---

### Post by GingerEskimo on 2012-06-24
In terms of hardware, i have a relatively old Advent 5301 notebook. 

2GB RAM, 1.73GHz core 2 duo etc. I think the chipset/integrated graphics it uses are notorious for being bad iirc. Looking to upgrade soon anyway.

results: 

```
> hal.1: read hal dataprocess 2926: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.eC0SacAaAQA
  Hardware Class: framebuffer
  Model: "Silicon Integrated 6330"
  Vendor: "Silicon Integrated Systems Corp."
  Device: "6330"
  SubVendor: "SiS"
  SubDevice: 
  Revision: "3.72.02"
  Memory Size: 128 MB
  Memory Range: 0xc0000000-0xc7ffffff (rw)
  Mode 0x031c: 1280x768 (+1280), 8 bits
  Mode 0x031d: 1280x768 (+2560), 16 bits
  Mode 0x031e: 1280x768 (+5120), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0304: 1024x768 (+128), 4 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x030d: 320x200 (+640), 15 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x0310: 640x480 (+1280), 15 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0313: 800x600 (+1600), 15 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0316: 1024x768 (+2048), 15 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0327: 320x240 (+320), 8 bits
  Mode 0x0328: 400x300 (+400), 8 bits
  Mode 0x0329: 512x384 (+512), 8 bits
  Mode 0x032a: 320x240 (+640), 16 bits
  Mode 0x032b: 400x300 (+800), 16 bits
  Mode 0x032c: 512x384 (+1024), 16 bits
  Mode 0x032d: 320x200 (+320), 8 bits
  Mode 0x0331: 640x400 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0302: 800x600 (+100), 4 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

---

### Post by carl4926 on 2012-06-24
SiS sucks
1024x798 is the best you'll get

---

### Post by GingerEskimo on 2012-06-25
Why is that? I don't understand, especially since i get 1280x768 on Windows7 on the same system. Guess i'll just have to deal with it, thanks anyway :)

---

### Post by carl4926 on 2012-06-25
> **GingerEskimo said:**
> Why is that? I don't understand, especially since i get 1280x768 on Windows7 on the same system. Guess i'll just have to deal with it, thanks anyway :)
Because SiS might support windows but not Linux
It's about the worst you could have had for graphics

---

