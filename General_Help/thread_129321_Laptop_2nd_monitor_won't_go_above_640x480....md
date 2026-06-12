---
title: "Laptop 2nd monitor won't go above 640x480..."
date: 2006-02-13
forum: General Help
---

### Post by thermans on 2006-02-13
The LCD on my laptop gets 1024x768 maximum resolution.  The external monitor is capable of 2048x1536.  (As is the video card).

But when I plug my external monitor in, both screens go to 640x480.  

What can I do about this?

This is what I see in the Xorg.0.log:

```
(WW) RADEON(0): Failed to detect secondary monitor DDC, default HSync and VRefresh used
```

Running "ddcprobe" fails when I'm in X-windows, which is probably why it can't detect the monitor:

```
vbe: VESA 2.0 detected.
oem: ATI MOBILITY RADEON 7500
memory: 32704kb
mode: 320x200x32k
mode: 320x200x64k
mode: 320x200x16m
mode: 1600x1200x256
mode: 640x400x256
mode: 640x480x256
mode: 640x480x32k
mode: 640x480x64k
mode: 640x480x16m
mode: 1600x1200x32k
mode: 800x600x256
mode: 800x600x32k
mode: 800x600x64k
mode: 800x600x16m
mode: 1600x1200x64k
mode: 1024x768x256
mode: 1024x768x32k
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x256
mode: 1280x1024x32k
mode: 1280x1024x64k
mode: 1280x1024x16m
edid: 
edidfail

```

But returns correctly when x-windows is not running (the above output minus the "edidfail" and this):

```
edid: 1 2
id: 5151
eisa: VSC5151
serial: d9da9b06
manufacture: 35 2000
input: separate sync, composite sync, sync on green, digital signal.
screensize: 40 30
gamma: 2.790000
dpms: RGB, active off, suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@72 Hz (VESA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@56 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@60 Hz (VESA)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 640x480@85
ctiming: 800x600@85
ctiming: 1024x768@85
ctiming: 1152x864@75
ctiming: 1280x960@60
ctiming: 1280x1024@85
ctiming: 1600x1200@60
ctiming: 1600x1200@75
monitorserial: SZ035151{n
monitorrange: 30-97, 50-180
monitorname: ViewSonic G8
monitorname: 0-4M
```

Any ideas?

---

### Post by Hellaxe on 2006-03-23
i´ve got the same problem using the radeon drivers on an ATI radeon 7500 M7 LW.
The most interesting thing is that the frequency, when the vga out cable is attached to the monitor or multimedia projector, is set to -1563hz. How is this possible???

---

