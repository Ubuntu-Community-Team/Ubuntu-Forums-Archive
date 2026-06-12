---
title: "X hangs &quot;EQ overflowing. The server is probably stuck in an infinite loop&quot;"
date: 2011-11-30
forum: General Help
---

### Post by IanWood on 2011-11-30
Hi,

I am using Kubuntu 11.10 and occasionaly X hangs - mouse still moves but nothing else works. 

Sometimes after a few mins it comes back, but then hangs again after a few seconds. I am not able to ctrl-alt-F1 to get a terminal either.

Here is the part of the Xorg log. 
```

[506641.626] 22: /usr/bin/X (0x400000+0x235ed) [0x4235ed]
[506817.875] [mi] EQ overflowing. The server is probably stuck in an infinite loop.
[506817.876] 
Backtrace:
[506817.876] 0: /usr/bin/X (xorg_backtrace+0x26) [0x460566]
[506817.876] 1: /usr/bin/X (mieqEnqueue+0x201) [0x45a941]
[506817.876] 2: /usr/bin/X (xf86PostMotionEventM+0xa3) [0x4805e3]
[506817.876] 3: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f3c81862000+0x5f23) [0x7f3c81867f23]
[506817.876] 4: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f3c81862000+0x65fb) [0x7f3c818685fb]
[506817.876] 5: /usr/bin/X (0x400000+0x6da77) [0x46da77]
[506817.876] 6: /usr/bin/X (0x400000+0x121f8e) [0x521f8e]
[506817.876] 7: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f3c96d79000+0x10060) [0x7f3c96d89060]
[506817.876] 8: /usr/lib/xorg/modules/drivers/m9x_drv.so (m9x8381+0x45) [0x7f3c93119f95]
[506817.876] 9: /usr/lib/xorg/modules/drivers/m9x_drv.so (m9x10834+0x32) [0x7f3c93119f22]
[506817.877] 10: /usr/lib/xorg/modules/drivers/m9x_drv.so (m9x14234+0x64) [0x7f3c93082574]
[506817.877] 11: /usr/lib/xorg/modules/drivers/m9x_drv.so (m9x26682+0x1f3) [0x7f3c93083843]
[506817.877] 12: /usr/lib/xorg/modules/drivers/m9x_drv.so (m9x2172+0x62) [0x7f3c93087742]
[506817.877] 13: /usr/lib/xorg/modules/drivers/m9x_drv.so (m9x29896+0x5b7) [0x7f3c9308f717]
[506817.877] 14: /usr/lib/xorg/modules/drivers/m9x_drv.so (m9x1290+0x382) [0x7f3c9308cf12]
[506817.877] 15: /usr/bin/X (0x400000+0xddde6) [0x4ddde6]
[506817.878] 16: /usr/bin/X (0x400000+0xa8de8) [0x4a8de8]
[506817.878] 17: /usr/bin/X (0x400000+0x16a00d) [0x56a00d]
[506817.878] 18: /usr/bin/X (BlockHandler+0x4a) [0x43390a]
[506817.878] 19: /usr/bin/X (WaitForSomething+0x11d) [0x45df7d]
[506817.878] 20: /usr/bin/X (0x400000+0x2f912) [0x42f912]
[506817.878] 21: /usr/bin/X (0x400000+0x232fe) [0x4232fe]
[506817.878] 22: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f3c95cb530d]
[506817.878] 23: /usr/bin/X (0x400000+0x235ed) [0x4235ed]

```

I am using a Matrox card with three screens. 

Anyone know what I could do?

Cheers

Ian

---

