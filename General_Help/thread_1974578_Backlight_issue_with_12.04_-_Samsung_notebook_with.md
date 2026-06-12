---
title: "Backlight issue with 12.04 - Samsung notebook with Nvidia Geforce 315M vga"
date: 2012-05-06
forum: General Help
---

### Post by adarsh_chacko on 2012-05-06
I've been unable to make the backlight brightness controls work after I've installed 12.04. I've followed a few tutorials for the fix, even installed packages from the samsung voria repo, followed all instructions from this post
[http://ubuntuforums.org/showthread.php?t=1966635&highlight=backlight](http://ubuntuforums.org/showthread.php?t=1966635&highlight=backlight)

Still haven't to make this work. Even when trying to reduce the backlight brightness from terminal using setpci does not work.

Though, if I pull out the power plug from the notepad, the backlight decreases automatically.

I work almost 12 hrs daily in front of the laptop and being unable to reduce the backlight makes my eyes tired very soon. Any kind of help is appreciated.

This is the relevant section from my lscpi -v output
---------------------------------------
02:00.0 VGA compatible controller: NVIDIA Corporation Device 0a7a (rev a2) (prog-if 00 [VGA controller])
        Subsystem: Samsung Electronics Co Ltd Device c581
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at dc000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at de000000 (64-bit, prefetchable) [size=32M]
        I/O ports at 2000 [size=128]
        [virtual] Expansion ROM at dd000000 [disabled] [size=512K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia_current, nouveau, nvidiafb

---

### Post by adarsh_chacko on 2012-05-08
Bump. Just wanted to check if anyone can help me with this. THanks

---

