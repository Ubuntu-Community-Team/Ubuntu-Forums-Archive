---
title: "Grub VGA code for 1680 x 1050 and more."
date: 2010-07-17
forum: General Help
---

### Post by quequotion on 2010-07-17
Just to make a thread that beats this one:
```
http://ubuntuforums.org/showthread.php?t=88416
``` which appears near the top of the list whenever I google this.


run this in a terminal: ```
sudo hwinfo --framebuffer
``` to get this ```
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.WHfzZmidTzC
  Hardware Class: framebuffer
  Model: "NVIDIA GT216 Board - 06810003"
  Vendor: "NVIDIA Corporation"
  Device: "GT216 Board - 06810003"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xcf000000-0xcfdfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768), 8 bits
  Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037b: 1280x720 (+5120), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits
```

add the hex after "Mode" at the end of a grub kernel line like this: 
```
kernel		/boot/vmlinuz-2.6.34-5-generic root=/dev/mapper/nvidia_dgcgcffh1 ro quiet splash vga=0x0369
```

for 1680x1050 use "vga=0x0369"

I'm reasonably sure that works with any kind of card that has a big enough framebuffer.

---

### Post by quequotion on 2010-08-20
Note: it is necessary to do this if you have an nvidia card and use plymouth for splash screen, unless you like your splash low-res and/or off-center.

Further note: the codes are not for nvidia, they are for grub. they should work just as well with nvidia, ati, or any other graphics card that supports the framebuffer size you want. the output of **hwinfo --framebuffer** will tell your capabilities.

---

