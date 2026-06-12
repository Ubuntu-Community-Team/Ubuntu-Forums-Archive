---
title: "Xorg segfaults, closes, and back to login screen"
date: 2012-08-07
forum: General Help
---

### Post by Killminusnine on 2012-08-07
Hey all, I've seen a few issues which were similar, but somehow seemed distinct from mine in this. In previous cases it's apparently been related to ubuntuone or xorg-evdev (that bug seems fixed) or something like that. 

I can't get Xorg to stop crashing at seemingly random times. This often (but not always) happens while I'm typing something (ANYWHERE, in a browser, vim, a chat window, anything).

The only logging I can find of this is in dmesg, I see this:

[34208.752461] Xorg[9983]: segfault at 9 ip b7690b28 sp bffea540 error 4 in Xorg[b7570000+1f3000]

Or something along those lines (and a similar message in syslog). Nothing of interest in Xorg's log.

Let's see, I  suppose other relevant information is that this is on a Lenovo Thinkpad L512, it has intel graphics, drivers. I've done nothing special with this, and as I said, it doesn't seem to matter what's running or what I'm doing.

Any advice?

---

### Post by Killminusnine on 2012-08-07
Oh, looks like it did throw something in Xorg.0.log. This is from the Xorg log

```

[ 34268.137]
Backtrace:
[ 34268.138] 0: /usr/bin/X (xorg_backtrace+0x37) [0xb76f8607]
[ 34268.138] 1: /usr/bin/X (0xb7570000+0x18c38a) [0xb76fc38a]
[ 34268.138] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb754d40c]
[ 34268.138] 3: /usr/bin/X (XIGetDeviceProperty+0x38) [0xb7690ce8]
[ 34268.138] 4: /usr/bin/X (0xb7570000+0x120d97) [0xb7690d97]
[ 34268.138] 5: /usr/bin/X (0xb7570000+0x1213ef) [0xb76913ef]
[ 34268.138] 6: /usr/bin/X (0xb7570000+0x116f77) [0xb7686f77]
[ 34268.138] 7: /usr/bin/X (0xb7570000+0x3791d) [0xb75a791d]
[ 34268.138] 8: /usr/bin/X (0xb7570000+0x2535a) [0xb759535a]
[ 34268.138] 9: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xf3) [0xb71d64d3]
[ 34268.138] 10: /usr/bin/X (0xb7570000+0x25699) [0xb7595699]
[ 34268.138] Segmentation fault at address 0xd
[ 34268.138]
Caught signal 11 (Segmentation fault). Server aborting
```

---

### Post by Killminusnine on 2012-08-08
Is there any other useful information I might provide? Sorry for the bump, but if I can't figure this out, I'll just install something else (currently, that'd be something of a pain).

---

