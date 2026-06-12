---
title: "XCB error"
date: 2011-10-18
forum: General Help
---

### Post by jamil.farooq@hotmail.com on 2011-10-18
hi there

 I have recently upgraded my system to ubuntu 11.10. And tried running flightgear with both fgrun utility and fgfs command too. i received this error:


./run_fgrun.sh
[xcb] Extra reply data still left in queue
[xcb] This is most likely caused by a broken X extension library
[xcb] Aborting, sorry about that.
fgrun: ../../src/xcb_io.c:575: _XReply: Assertion `!xcb_xlib_extra_reply_data_left' failed.
Aborted

kindly help me out with the problem

---

### Post by jamil.farooq@hotmail.com on 2011-10-18
also i have ATI RADEON graphics driver... when i go additional driver for proprietary drivers i got list of two drivers out of that  i can't install one with (post-release updates)... i think this is causing me trouble ... please help me out

---

### Post by zeropointer on 2011-10-30
I found the info/fix from:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/877445](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/877445)

It's an issue with Catalyst 11.8 drivers:

> I've tested Catalyst 11.9 from the AMD website last night (fglrx 8.892), and managed to get wine working with that.
It is still unclear to me if the issue lies in a library incompatibility    (wrong libGL being picked, lib32 issue, etc.) or a bug in Catalyst. I    used the installer script and made sure everything is in place   manually.> it seems wine is now picking up a libGL.so.1   that actually works. Most  likely, it's the one from mesa   (libgl1-mesa-glx). That one doesn't have  this nasty XCB   bug.> applications call libGL.so from /usr/lib32   open(&quot;/usr/lib32/libGL.so&quot;, O_RDONLY)   which is a  symlink to  mesa/libGL.so.1 and not /usr/lib32/fglrx/libGL.so.1 !!
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

### Post by zeropointer on 2011-11-14
Just in case someone is looking for a solution to this problem.
It's also similar to this problem:
[http://ubuntuforums.org/showthread.php?p=11455021#post11455021]("http://ubuntuforums.org/showthread.php?p=11455021#post11455021")

I believe he has a 32bit system where I have a 64bit, hence the different location of the problem. So, change accordingly:
> it was my /usr/lib instead of /usr/lib32 that had the issue

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

