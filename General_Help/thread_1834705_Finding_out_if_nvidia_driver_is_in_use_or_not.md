---
title: "Finding out if nvidia driver is in use or not"
date: 2011-08-27
forum: General Help
---

### Post by espartano on 2011-08-27
Hello!

I'm having a tough time installing nvidia drivers! In previous versions, i would use the 'proprietary drivers' thing and it would install the current version of nvidia drivers for me.

But now I'm always getting the "the driver is activated but not in use". 

I'm using a Dell Vostro 1400 with 8400M. 

I've purged all nvidia and nouveau stuff, and reinstalled from scratch on the terminal, but still cant figure out if it's being used or not!

The "proprietary driver" still says that it's not in use, and I'm getting some choppy animations, but since my card is pretty old, maybe it's the way it's suposed to be.

lspci says:


01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (re
v a1) (prog-if 00 [VGA controller])
        Subsystem: Dell Device 0227
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at ef00 [size=128]
        [virtual] Expansion ROM at fc000000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia-173, nouveau, nvidiafb

So, should I trust lspci, is it in use? 

Thanks!

---

### Post by wojox on 2011-08-27
It appears your using the 173.xx.xx. 

What version Ubuntu are you running?

---

### Post by espartano on 2011-08-28
Hi! I'm running Ubuntu 11.04, just installed it this afternoon.

I switched to Unity 2D, seems a lot faster now, and since I was trying to disable transparencies and stuff, I believe I'll just stick with 2D!

Only thing I'm missing is the super + w, which doesn't seem to work, and being able to change the launcher width, that doesn't seem possible on Unity-2D yet! 

Thanks!

---

