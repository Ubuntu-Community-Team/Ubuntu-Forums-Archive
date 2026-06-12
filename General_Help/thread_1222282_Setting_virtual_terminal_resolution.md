---
title: "Setting virtual terminal resolution"
date: 2009-07-24
forum: General Help
---

### Post by m_ad on 2009-07-24
I have a Samsung SyncMaster 931BW with a native resolution of 1440x900. This isn't listed in System->Administration->Startup Manager.

Is there a way to add this resolution manually in /boot/grub/menu.lst?

This mode isn't listed in the [Ubuntu Documentation]("https://help.ubuntu.com/community/ChangeTTYResolution").

And.. the resolution isn't listed in hwinfo

```
[matt@matt-desktop:~]$ sudo hwinfo --framebuffer
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.447]
  Unique ID: rdCR.2NlRmnESudA
  Hardware Class: framebuffer
  Model: "NVIDIA Crush50 Board - c51pvg0 "
  Vendor: "NVIDIA Corporation"
  Device: "Crush50 Board - c51pvg0 "
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 64 MB
  Memory Range: 0xe0000000-0xe3ffffff (rw)
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
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

EDIT: also, why does this resolution not apply to the actual grub menu? It only applies after I select a boot option.

---

### Post by m_ad on 2009-07-25
Anyone know?

---

### Post by CatKiller on 2009-07-25
You can only select one of the [VESA modes]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Other_commonly_available_modes") that are natively supported by your graphics adaptor. Since the standard only specified a small number of modes if you want a non-standard mode you have to hope that the manufacturer of your graphics adaptor chose to put support for that mode in. There are a number of newer modes that aren't supported by all of the graphics adaptors available. But you might get lucky.

---

### Post by m_ad on 2009-07-26
Thanks. 1440x900's gotta be supported by my video card if I'm using it in Gnome, right? In that case, can I just use the code that corresponds to that resolution on the page you listed?

---

### Post by CatKiller on 2009-07-26
> **m_ad said:**
> Thanks. 1440x900's gotta be supported by my video card if I'm using it in Gnome, right? 

Not necessarily. Using the one of the built-in modes means that the graphics card is handling all the video timings, all the software does is say "use built-in mode number 356." When you're running X all the video timings are handled by the graphics driver. The software does everything.

> 
In that case, can I just use the code that corresponds to that resolution on the page you listed?

Maybe. If the mode is supported, it will work. If it isn't, you'll have to pick a different one that doesn't look too bad.

---

### Post by m_ad on 2009-07-26
Thanks for your help CatKiller, in both threads :)

---

