---
title: "tty does not appear"
date: 2010-08-05
forum: General Help
---

### Post by Dobro_player on 2010-08-05
Hi everybody,
If I press ctrl-alt-F1 through to F6 there is only a blinking line cursor, and no tty terminal. I can get a terminal (like Konsole) in X though. Any ideas as to why this is happening?

---

### Post by oldos2er on 2010-08-05
Possibly a bug in your video drivers. What video card do you have, and are you running the latest drivers for it?

---

### Post by Dobro_player on 2010-08-05
I put in "lspci -v" and I think these are the graphics parts: 
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
        Subsystem: Dell Device 02b0
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at f0300000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Dell Device 02b0
        Flags: bus master, fast devsel, latency 0
        Memory at f0080000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

```

---

