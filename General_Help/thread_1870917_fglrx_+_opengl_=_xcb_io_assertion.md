---
title: "fglrx + opengl = xcb_io assertion"
date: 2011-10-28
forum: General Help
---

### Post by Sheado on 2011-10-28
Hi All,

After updating to Oneiric, I now get this any time I try to run anything with OpenGL or hardware acceleration:
> name of display: :0
[xcb] Extra reply data still left in queue
[xcb] This is most likely caused by a broken X extension library
[xcb] Aborting, sorry about that.
glxinfo: ../../src/xcb_io.c:575: _XReply: Assertion `!xcb_xlib_extra_reply_data_left' failed.
Aborted
I've tried re-installing fglrx in all the ways I know of (via jockey-kde, apt-get fglrx, drivers from the ati site, etc.). I've also tried dpkg-reconfigure and apt-get --reinstall on libglib2.0-0 with no luck. 

Other than opengl, everything else seems to work with the fglrx driver. So I'm starting to think this may be due to either a bug in xcb or a corrupt Oneiric upgrade.

Any suggestions? 
Thanks!

---

### Post by zeropointer on 2011-10-30
I found the info/fix from:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/877445](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/877445)

It's an issue with Catalyst 11.8 drivers:

> I've tested Catalyst 11.9 from the AMD website last night (fglrx 8.892), and managed to get wine working with that.
It is still unclear to me if the issue lies in a library incompatibility   (wrong libGL being picked, lib32 issue, etc.) or a bug in Catalyst. I   used the installer script and made sure everything is in place  manually.> it seems wine is now picking up a libGL.so.1  that actually works. Most  likely, it's the one from mesa  (libgl1-mesa-glx). That one doesn't have  this nasty XCB  bug.> applications call libGL.so from /usr/lib32  open(&quot;/usr/lib32/libGL.so&quot;, O_RDONLY)   which is a symlink to  mesa/libGL.so.1 and not /usr/lib32/fglrx/libGL.so.1 !!
I went to /usr/lib32
```
cd /usr/lib32
```I did
```
ls -ln libGL*
```to show me the symbol links.

I changed libGL.so to point to /usr/lib32/fglrx/libGL.so.1 (first backing up)
```
sudo mv libGL.so libGL.so.bak
sudo ln -s /usr/lib32/fglrx/libGL.so.1 /usr/lib32/libGL.so
```that didn't work, so I tried:
```
sudo mv libGL.so.1 libGL.so.1.bak
sudo ln -s /usr/lib32/fglrx/libGL.so.1 /usr/lib32/libGL.so.1
```linking libGL.so.1 to /usr/lib32/fglrx/libGL.so.1

(You can do:
ls -ln libGL* 
to see if the links are working)
With that, I got pass the problem. Although it seems I have other problems now.
I hope that works/helps.

---

### Post by Sheado on 2011-11-02
zeropointer - you are awesome!

thanks, that worked (more specifically it was my /usr/lib instead of /usr/lib32 that had the issue)

thanks again!

---

### Post by zeropointer on 2011-11-14
I'm glad it worked for you.

Small update:
For some reason the symbolic link didn't stick.
So, I made the libGL.so.1.2 point to fglrx/libGL.so.1 instead:
(backing up first)
The trick was to move libGL.so.1.2 away from that folder so it wouldn't relink to it.

```
cd /usr/lib32/
sudo mv libGL.so.1.2 ~/libGL.so.1.2.bak
sudo ln -s /usr/lib32/fglrx/libGL.so.1 /usr/lib32/libGL.so.1.2
```

Once again, thanks to the guys/info/fix from:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/877445]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/877445")

---

### Post by Sheado on 2011-11-17
Thanks zeropointer,

apt-get was changing the link for me every time I got an update (even if unrelated).
This solution seems to have stuck so far.

:p

---

### Post by NahsiN on 2011-11-24
Thanks Zeropointer for that solution. I had just bought the humble indie bundle and tried to run crayon physics game and I also got these xcb errors.
> [xcb] Extra reply data still left in queue
[xcb] This is most likely caused by a broken X extension library
[xcb] Aborting, sorry about that. I have catalyst 11.11 installed but this problem still persisted. Now I am no linux guru and I just wanted my game to work. Your code did the trick. Thank you very much...Hope this will help out more people who will buying the humble indie bundle over the next coming days and running into the same problem as me if they are running fglrx.

---

