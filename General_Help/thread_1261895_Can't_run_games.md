---
title: "Can't run games"
date: 2009-09-09
forum: General Help
---

### Post by KajaK on 2009-09-09
Hi.

Lately I installed a game called supertux 2. Suddently I wasn't able to run the game anymore. Afterwards I installed to other games just to try if I could get them running, but still without any luck. When i open supertux 2 in terminal i get the following:

kajak@LGE300:~$ supertux2
[/home/kajak/.supertux2] is in the search path
[/usr/share/games/supertux2] is in the search path
Invalid button '0' in buttonmap
Invalid button '1' in buttonmap
Invalid axis '-2' in axismap
Invalid axis '-1' in axismap
Invalid axis '1' in axismap
Invalid axis '2' in axismap
X Error of failed request: BadRequest (invalid request code or no such operation)
Major opcode of failed request: 143 (GLX)
Minor opcode of failed request: 19 (X_GLXQueryServerString)
Serial number of failed request: 11
Current serial number in output stream: 11
Locking assertion failure. Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb74a47c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb74a496e]
#2 /usr/lib/libX11.so.6 [0xb74eb619]
#3 /usr/lib/libX11.so.6(XSync+0x25) [0xb74df625]
#4 /usr/lib/libSDL-1.2.so.0 [0xb7eaeb25]
#5 /usr/lib/libSDL-1.2.so.0 [0xb7eb7bbb]
#6 /usr/lib/libSDL-1.2.so.0(SDL_VideoQuit+0x50) [0xb7ea5940]
#7 /usr/lib/libSDL-1.2.so.0(SDL_QuitSubSystem+0x55) [0xb7e7a7d5]
#8 /usr/lib/libSDL-1.2.so.0(SDL_Quit+0x1e) [0xb7e7a85e]
#9 /lib/tls/i686/cmov/libc.so.6(exit+0x89) [0xb77fdd89]
#10 /usr/lib/libX11.so.6 [0xb74e3d4e]
#11 /usr/lib/libSDL-1.2.so.0 [0xb7eb74f6]
#12 /usr/lib/libX11.so.6(_XError+0x109) [0xb74e3ef9]
#13 /usr/lib/libX11.so.6(_XReply+0x22e) [0xb74ec46e]
#14 /usr/lib/libGL.so.1 [0xb7e25337]
#15 /usr/lib/libGL.so.1 [0xb7e06ab4]
#16 /usr/lib/libGL.so.1(glXChooseVisual+0x37) [0xb7e03b97]
#17 /usr/lib/libSDL-1.2.so.0 [0xb7eb3ce1]
#18 /usr/lib/libSDL-1.2.so.0 [0xb7eba046]
#19 /usr/lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1f0) [0xb7ea6900]
XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ""
after 15 requests (14 known processed) with 0 events remaining.



Regards Kasper

---

### Post by shae on 2009-09-09
Do you have direct rendering working?

```
glxinfo | grep direct
```

---

### Post by KajaK on 2009-09-09
Hmm.. doesn't look that way:


kajak@LGE300:~$ glxinfo | grep direct
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

---

### Post by NoaHall on 2009-09-09
Try rebuilding your xorg file (dpkg-reconfigure -phigh xserver-xorg), if that doesn't fix it, try using "sudo ldconfig" and if that fails, you need to try and get a different version of X/video card.

---

### Post by KajaK on 2009-09-09
Got it working... my graphic card wasn't activated for some reason. Thanks for the help. Wouldn't have guest it without.

---

### Post by shae on 2009-09-09
> **KajaK said:**
> Got it working... my graphic card wasn't activated for some reason. Thanks for the help. Wouldn't have guest it without.

That is great to hear!  Let us know if you have any other problems.

---

