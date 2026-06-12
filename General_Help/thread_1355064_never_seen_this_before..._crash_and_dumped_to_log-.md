---
title: "never seen this before... crash and dumped to log-in screen"
date: 2009-12-14
forum: General Help
---

### Post by Choad on 2009-12-14
ok this is my dad's computer, i've set him up with 9.10. 3 times now he has been playing solitaire (with no other applications running at all, bar whatever services run by default) and the system will jump to a console login prompt, then a few seconds later will bring up the gui login screen.

it's annoying enough having this happen while playing a game but i imagine he'd be rather more annoyed if he was actually doing some work.

i've been trying to look through the system logs but nothing has jumped out at me yet... i don't really know where to look tho.

i am really going to need some help getting this sorted, does anyone have any advice? what logs should i be looking at?

---

### Post by xtjacob on 2009-12-14
What it sounds like is that gnome, or x is chrashing for some reason.

---

### Post by Choad on 2009-12-14
i have a feeling that this

```

(WW) intel(0): i830_uxa_prepare_access: bo map failed

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133d6b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7d35]
2: [0x7aa400]
3: /usr/lib/xorg/modules//libfb.so(fbCopyNtoN+0x24c) [0x34f7cc]
4: /usr/lib/xorg/modules/drivers//intel_drv.so(uxa_copy_n_to_n+0x74a) [0x3019fa]
5: /usr/lib/xorg/modules//libfb.so(fbCopyRegion+0x21b) [0x34e76b]
6: /usr/lib/xorg/modules//libfb.so(fbDoCopy+0x44d) [0x34ec8d]
7: /usr/lib/xorg/modules/drivers//intel_drv.so(uxa_copy_area+0x98) [0x301258]
8: /usr/bin/X [0x8181593]
9: /usr/bin/X(ProcCopyArea+0x165) [0x808b4c5]
10: /usr/bin/X(Dispatch+0x35f) [0x808d17f]
11: /usr/bin/X(main+0x395) [0x8072515]
12: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xa76b56]
13: /usr/bin/X [0x80719c1]
Saw signal 11.  Server aborting.

```

might be trying to tell me why it all went to crap but i dont really know what it means

i googled "i830_uxa_prepare_access: bo map failed" and got some hits describing similar problems

i shall continue googling...

---

### Post by Choad on 2009-12-14
jackpot. [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/444518](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/444518)

same exact bug

so in reading the comments on the bug report i have discovered that i am not alone in this, and also that no one seems to have a fix, or if they do they are keeping quiet about it

joy.

---

### Post by jaygo on 2010-01-21
I had the same result but it wasn't related to any games. Had a lot of apps running but was just typing in a browser when it dumped. 

How did you pull that log? The only error I can find in the logs is that virtualbox had an issue about a minute prior.

===========
Looks like my crash is related to something else: [https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/475867]("https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/475867")

---

