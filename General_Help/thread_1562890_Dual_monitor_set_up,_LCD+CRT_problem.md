---
title: "Dual monitor set up, LCD+CRT problem"
date: 2010-08-28
forum: General Help
---

### Post by Cant on 2010-08-28
I have just set up a temporary dual monitor with my laptop and an old Grundig CRT monitor with speakers. Everything has worked so far but the CRT is in black and white and there is no audio.

---

### Post by Cant on 2010-08-29
bump

---

### Post by Cant on 2010-08-30
Bump, really need this solved.

---

### Post by realzippy on 2010-08-30
Have you more infos?Graphics card?Driver?Ubuntu version?

Sounds like using the s-video port...

---

### Post by ctsdownloads on 2010-08-30
What is the laptop involved? Without this, it's kind of like going to the mechanic and saying the car is broken. ;)

I am assuming it's either VIA or Intel based for video on the notebook? If it's via, good luck. If Intel or NVIDIA/ATI and you are getting an image, then it sounds like it's "working" but the monitor's data is not being interpreted, can't help much there.

In most cases, it's either great or non-existent with VGA from the laptop. Sounds like you hit in the middle there somewhere.

As for audio, only speakers in a monitor I've ever seen had an attached cable to plug into the soundcard of the computer. Don't believe a VGA cable has the ability to transmit sound without it.

---

### Post by Cant on 2010-08-30
> What is the laptop involved?
The laptop is used as the primary monitor with the CRT being used to play HD video for my mom -_-

> I am assuming it's either VIA or Intel based for video on the 
notebook?
It's an ATI video card and an nVidia controller, I beleive.

> In most cases, it's either great or non-existent with VGA from the laptop. Sounds like you hit in the middle there somewhere.
wat

The audio has been taken care of, but the monitor is still B&W.

---

### Post by realzippy on 2010-08-30
Open

Applications -> Accessories -> Terminal

can you post ouput from:

```
lspci | grep VGA
```

---

### Post by Cant on 2010-08-31
> **realzippy said:**
> Open

Applications -> Accessories -> Terminal

can you post ouput from:

```
lspci | grep VGA
```

```
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
```

---

### Post by realzippy on 2010-08-31
Have you installed any nvidia drivers?

System/Administration/HardwareDrivers?

---

### Post by Cant on 2010-08-31
> **realzippy said:**
> Have you installed any nvidia drivers?

System/Administration/HardwareDrivers?

Yes, NVIDIA accelerated graphichs driver (version current).

---

### Post by realzippy on 2010-08-31
Run
```
sudo nvidia-bug-report.sh
```

creates a bug report in your home folder,please post this.

Have you ever run nvidia-settings and tried to configure your monitors ?

---

### Post by Cant on 2010-09-01
> **realzippy said:**
> Run
```
sudo nvidia-bug-report.sh
```
 
creates a bug report in your home folder,please post this.
 
Have you ever run nvidia-settings and tried to configure your monitors ?
 
I always use nvidia-settings.
Bug report has been made.

---

### Post by realzippy on 2010-09-01
```
**) Aug 30 21:03:36 NVIDIA(0): TwinView enabled
(II) Aug 30 21:03:36 NVIDIA(0): Display Device found referenced in MetaMode: DFP-0
(WW) Aug 30 21:03:36 NVIDIA(0): [COLOR="Red"]TwinView requested, but only 1 display devices found[/COLOR].
(II) Aug 30 21:03:36 NVIDIA(0): Assigned Display Device: DFP-0
(WW) Aug 30 21:03:36 NVIDIA(0): Invalid display device in Mode Description
(WW) Aug 30 21:03:36 NVIDIA(0):     "TV:nvidia-auto-select+1280+0"
(WW) Aug 30 21:03:36 NVIDIA(0): Not using mode description "TV:nvidia-auto-select+1280+0";
(WW) Aug 30 21:03:36 NVIDIA(0):     unable to map to display device
(II) Aug 30 21:03:36 NVIDIA(0): Validated modes:
(II) Aug 30 21:03:36 NVIDIA(0):     "TV:nvidia-auto-select+1280+0,DFP:nvidia-auto-select+0+0"
(II) Aug 30 21:03:36 NVIDIA(0): Virtual screen size determined to be 1280 x 800
(--) Aug 30 21:03:36 NVIDIA(0): DPI set to (98, 96); computed from "UseEdidDpi" X config
(--) Aug 30 21:03:36 NVIDIA(0):     option
(==) Aug 30 21:03:36 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Aug 30 21:03:36 NVIDIA(0): Initialized GPU GART.
(II) Aug 30 21:03:36 NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) Aug 30 21:03:36 NVIDIA(0):     enough to receive ACPI hotkey events.
(WW) Aug 30 21:03:36 NVIDIA(0): ACPI: Error: Unable to find the brightness file path under
(WW) Aug 30 21:03:36 NVIDIA(0):     /proc/acpi/video. The NVIDIA X driver will not be able to
(WW) Aug 30 21:03:36 NVIDIA(0):     respond to ACPI brightness change hotkey events.
(II) Aug 30 21:03:36 NVIDIA(0): Setting mode
(II) Aug 30 21:03:36 NVIDIA(0):     "TV:nvidia-auto-select+1280+0,DFP:nvidia-auto-select+0+0"
```

...some warnings concerning unusual modelines and only 1 device ??
seems as only your internal display is recognized by the driver...

---

