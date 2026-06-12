---
title: "Xlib:  extension &quot;NV-GLX&quot; missing on display &quot;localhost:1.0&quot;"
date: 2010-11-25
forum: General Help
---

### Post by emoguitarist06 on 2010-11-25
I am running **Ubuntu Maverick x64** and I have maverick x86 installed on a separate partition so I can run pcsx2 (a playstation 2 emulator that **only** works in 32bit)

When I **boot into **32bit Maverick I can run pcsx2 but what I WANT to do is **run it via chroot in my 64bit enviorment**. I can successfully chroot and start pcsx2 but the problem occurs with my X window

I use
```
Xephyr -ac -fullscreen :1
```
per the advice from here: [http://wiki.mandriva.com/en/Development/Howto/Chroot#Using_Xephyr](http://wiki.mandriva.com/en/Development/Howto/Chroot#Using_Xephyr) (except I added the "-fullscreen")
**to start an X session for my chroot to use**

THEN I use
```
export DISPLAY=localhost:1
```
**to tell my chroot to use the new display for any gui application**

PCSX2 crashes or is "KILLED" and I believe this error message is the main problem Xlib:  extension "NV-GLX" missing on display "localhost:1.0"

**[COLOR="Red"]I attached 3 screenshots and the outputs of the terminals[/COLOR]**
(the last screen shot shows the X window all black because pcsx2 ended itself)

---

### Post by emoguitarist06 on 2010-11-26
Bump

---

