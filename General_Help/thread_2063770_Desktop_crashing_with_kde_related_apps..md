---
title: "Desktop crashing with kde related apps."
date: 2012-09-27
forum: General Help
---

### Post by davemar on 2012-09-27
I'm starting a new thread on this one, as I originally ask about rosegarden causing the problem, but it appears more general as many application do it.

When I run some applications (mostly KDE derived ones it seems) the whole desktop will crash, returning me to the login screen. For example, rosegarden will cause this crash when selecting the open file option.

I'm running 12.04 64-bit with gnome desktop, but it does the same with the unity desktop too. I'm using NVIDIA graphics drivers (the latest ones).

I think I'm getting clues from the Xorg.0.log.old file:
```

Backtrace:
[   910.000] 0: /usr/bin/X (xorg_backtrace+0x26) [0x7f1b2b01a876]
[   910.000] 1: /usr/bin/X (0x7f1b2ae92000+0x18c71a) [0x7f1b2b01e71a]
[   910.000] 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f1b2a1b8000+0xfcb0) [0x7f1b2a1c7cb0]
[   910.000] 3: /usr/bin/X (doListFontsWithInfo+0x10b) [0x7f1b2aee12db]
[   910.000] 4: /usr/bin/X (ProcessWorkQueue+0x21) [0x7f1b2aee4ad1]
[   910.000] 5: /usr/bin/X (WaitForSomething+0x65) [0x7f1b2b017b25]
[   910.000] 6: /usr/bin/X (0x7f1b2ae92000+0x4e5f2) [0x7f1b2aee05f2]
[   910.000] 7: /usr/bin/X (0x7f1b2ae92000+0x3d7ba) [0x7f1b2aecf7ba]
[   910.000] 8: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f1b2904d76d]
[   910.000] 9: /usr/bin/X (0x7f1b2ae92000+0x3daad) [0x7f1b2aecfaad]
[   910.000] Segmentation fault at address 0x10
[   910.000] 
Caught signal 11 (Segmentation fault). Server aborting

```

which appears to be the time of crash. 

Has anyone seen anything like this before, and know what's causing it and got a solution?

---

### Post by davemar on 2012-09-27
Permission to feel smug :)

I think I've cracked it. In xorg.conf, there are these lines:
```

Section "Files"
    FontPath        "unix/:7100"
EndSection

```
I commented these out, and now the crashing appears to have gone!

---

