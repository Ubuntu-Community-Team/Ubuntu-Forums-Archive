---
title: "How can I speed up GTK redraws?"
date: 2009-07-08
forum: General Help
---

### Post by Gullible Jones on 2009-07-08
There is an annoying issue that has been bugging me for a long time on Ubuntu (and many other "desktop" distributions):

[[img]http://xs841.xs.to/xs841/09283/artifacts815.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs841&d=09283&f=artifacts815.png)

Drag one GTK application across another GTK application, and you get artifacts on the second window, like the ones in the screenshot. The heavier the applications, the worse the artifacts. This doesn't impact usability a whole lot, but it drives me quite batty.

I've also noticed that, on stock Debian, it's much less visible. I actually get less of this artifacting on Debian with a full Gnome desktop than on Xubuntu.

So, figuring there has to be some setting that can change this, I've tried all kinds of things... Enabling UXA, enabling XAA (which caused a kernel oops), switching to different GTK themes... Nothing worked. I tried compositing managers, and those just slowed my desktop down to the point of unusability.

(Funny, that... On Windows you get fast compositing *with no hardware acceleration at all.* I wonder how they do that.)

Is there any way - any way at all - that I can fix these slow redraws, without using a compositing manager? Environment variables? Compile settings? Anything? There must be some way of doing it; I just have trouble believing that Ubuntu users necessarily have to put up with this in 2009, when users of Windows, MacOS, and even some other Linux distros don't.

---

### Post by CatKiller on 2009-07-08
> **Gullible Jones said:**
> (Funny, that... On Windows you get fast compositing *with no hardware acceleration at all.* I wonder how they do that.)

No you don't.

> I just have trouble believing that Ubuntu users necessarily have to put up with this in 2009, when users of Windows, MacOS, and even some other Linux distros don't.

They don't. There's something screwy with your setup. I've not seen, nor heard of anyone else seeing, anything like that.

---

### Post by Jebtrix on 2009-07-08
> **catkiller said:**
> no you don't.



They don't. There's something screwy with your setup. I've not seen, nor heard of anyone else seeing, anything like that.

+1

---

### Post by BlackRoijaX on 2009-07-08
I've had that issue on Linux & Windows.

It's pretty common.

---

