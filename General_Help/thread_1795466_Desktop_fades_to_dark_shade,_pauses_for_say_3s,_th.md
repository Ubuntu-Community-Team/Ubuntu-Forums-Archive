---
title: "Desktop fades to dark shade, pauses for say 3s, then returrns"
date: 2011-07-02
forum: General Help
---

### Post by finny388 on 2011-07-02
Every .5 to 3 hours, the desktop will make a gradual reduction of brightness, stay this way for 2-3 seconds, then return return to normal.

During this the screen does not freeze, audio/video continues, but it will not accept kb/mouse input.

I basically only surf and watch videos. I've never seen it while using VLC, only in Firefox (now at v5)

This is new since going to 11.04.
I'm using my Samsung LCD TV as monitor (and have been for a long time)

Anyone seen this before? thx

eeepc 900
celeron 900
2GB ddr2

---

### Post by wildmanne39 on 2011-07-02
> **finny388 said:**
> Every .5 to 3 hours, the desktop will make a gradual reduction of brightness, stay this way for 2-3 seconds, then return return to normal.

During this the screen does not freeze, audio/video continues, but it will not accept kb/mouse input.

I basically only surf and watch videos. I've never seen it while using VLC, only in Firefox (now at v5)

This is new since going to 11.04.
I'm using my Samsung LCD TV as monitor (and have been for a long time)

Anyone seen this before? thx

eeepc 900
celeron 900
2GB ddr2
The screen doing that is while something slow is processing, that is why it is set to do when an application is taking a while to load or work. I get that to sometimes and it is just a matter of waiting for the application to finish.

---

### Post by finny388 on 2011-07-03
Thanks. Makes sense.

But fading in and out - is that a linux thing?

---

### Post by wildmanne39 on 2011-07-04
> **finny388 said:**
> Thanks. Makes sense.

But fading in and out - is that a linux thing?Hi, yes there is a setting for that but I do not remember where and what it is called.

---

### Post by RedRat on 2011-07-04
I run 8.04 on Dell with 2Gb of memory and sometime it will do this with Firefox when a page has a lot of graphics on it. It may be part of the cache. I am running 10.04 on a System75 with 6Gb and have not yet seen that problem. I suspect it is a matter of memory.

---

### Post by finny388 on 2011-07-11
well it seems like an elegant way to show you the pc is busy

sure beats the hourglass or nothing in windows

wish it was geekier and text faded in saying "CPU busy" or "RAM full". just a thought
over time you'd know your bottle necks and how to upgrade.

---

### Post by arizonalarry2 on 2011-07-25
Happens to my FireFox all the time when I do a Google image search, also happens in my desktop windows when I move a large number of files from one directory to another. Usually grays out for a minute or so. I just switch to another desktop and do something else while it finishes.

---

### Post by jwbrase on 2011-07-25
> **finny388 said:**
> well it seems like an elegant way to show you the pc is busy

sure beats the hourglass or nothing in windows

wish it was geekier and text faded in saying "CPU busy" or "RAM full". just a thought
over time you'd know your bottle necks and how to upgrade.

Except it's not always a matter of the machine itself being bogged down. Sometimes it's just that an application is misbehaving (or unresponsive for some other reason). Where Windows will describe a process as "(not responding)", Compiz will fade its window to gray.

---

### Post by jwbrase on 2011-07-25
> **finny388 said:**
> But fading in and out - is that a linux thing?

Not specifically. It's a Compiz thing. Linux is just the kernel for Ubuntu (or any other Linux distribution) and doesn't actually do any graphical stuff itself. Most distributions use a set of programs, generally including some implementation of the X Window System, to provide the GUI. On Ubuntu, this group of programs also includes Compiz, which acts as a window manager and provides various graphical effects, including the whole "fade unresponsive programs to grey" thing.

In theory, Compiz can run on any Unix-like OS that has an implementation of the X Window System installed (subject to the hardware being good enough to run it). This includes MacOS X (I'm not sure if it has an X implementation pre-installed, but I know they exist for it), though it would only affect programs made to run under the XWS, and not any using the native Mac GUI. (I've only personally used Compiz on Linux, though).

It is also theoretically possible to run it on Windows with a Unix compatibility layer like Cygwin and an X server like Xming or Cygwin X, but I haven't had too much luck with Windows X servers, so that "theoretically possible" might very well not bear out in practice.

---

