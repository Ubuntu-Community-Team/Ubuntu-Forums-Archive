---
title: "Different bulds - very different performances. Why?"
date: 2011-11-20
forum: General Help
---

### Post by zcacogp on 2011-11-20
Hello, 

I have a machine which has two different Ubuntu builds on it. They live on different partitions of different hard drives, and were built by different means. The machine is clearly the same - 64-bit AMD with a decent slug (4Gb I think) of RAM. 

The first one started life as an 11.10 64-bit Oneiric Ubuntu build, but I decided I wasn't getting along with Unity so I put a KDE front end on it. This has never worked properly, with graphics performance being slow and occasional freezes. It won't allow me to run some of the more esoteric desktop effects (exploding windows, for instance), and is generally only borderline usable. I have tried a number of things with this, mainly 'round updating the video driver to the latest proprietry one (thread here: [http://ubuntuforums.org/showthread.php?t=1878652](http://ubuntuforums.org/showthread.php?t=1878652), with many thanks to MoreOrLess for his help), although this didn't make much difference. 

The second one was a dedicated 11.10 64-bi tOneiric Kubuntu build from the outset, and works much better. The desktop is much smoother, it is much (much) quicker, and compared with the first one it is a joy to use. It is lovely in almost every respect, and uses the Open Source ATI graphics driver. The only snag is that if you try and create a new panel on the desktop it crashes, so I am forced to have the default layout with the panel at the bottom. Not the end of the world, but I'd like it to be otherwise. 

Both of these appear as different boot options at GRUB (along with a Windows XP install). 

So I have two questions. Firstly, why can two different builds on the same machine have such different end results? What can I do to make the first build run as smoothly and beautifully as the second one? Secondly, how can I create a new panel on the desktop with the second build without it crashing? (I suspect that this second question may have to have a thread on it's own - unless it's already been answered elsewhere, although google didn't find one for me.) 

Any suggestions? 

Thanks, in advance, for any help. 


Oli.

---

### Post by zcacogp on 2011-11-25
Anyone have any ideas? 

As an update to my earlier posting, the second build is now running poorly as well; it is getting jerky, the same screen artefacts are appearing as were in the first build, and it is no longer pleasant to use. I turned the machine on and used it for about 90 minutes this morning, then left it for about 3 hours, and when I returned to it I found it unusuable; froze regularly, mouse movement very jerky, window opening impossibly slow. I gave up when it froze for more than 2 minutes and forced a reboot ... 

Surely this isn't right? Ubuntu 11.04 wasn't this bad (although I had to move back to Gnome as Unity didn't work for me), and I suspect that the current build isn't going to pass the test of time. 

How can I get to the bottom of these performance issues? 

All help welcomed - thanks. 


Oli.

---

### Post by Paddy Landau on 2011-11-26
Your problems sound as though there is something wrong with the graphics driver. I presume everything works fine on Windows?

As you are using Windows XP, you seem to have an older machine.

As an experiment, how about replacing your first installation (the one with the modified Gnome -> KDE desktop) with [Lubuntu]("https://wiki.ubuntu.com/Lubuntu"). Lubuntu is extremely light and fast. If you still get problems with Lubuntu, we know there is something going on at the Linux level, presumably (but not necessarily) the graphics driver. If Lubuntu works, it's an Ubuntu (or Kubuntu) problem.

If Lubuntu works, you can consider using [Xubuntu]("http://www.xubuntu.org/"); not as light as Lubuntu, nor as heavy as Ubuntu, but "prettier" and more flexible than Lubuntu.

---

### Post by zcacogp on 2011-11-26
Paddy, 

Thanks - that sounds like a sensible way into it. Yes, everything works fine on XP (which is one of the annoying things; while I dramatically much prefer Ubuntu to XP, at least XP worked well and didn't freeze up.) The machine isn't that old - it's a twin-core 2.9GHz AMD. (I have a legit copy of XP from yonks ago, which I have used for a number of machines of mine.) I doubt that it's an issue of processing power that is causing the issue, although see the logic in your experiment. 

I'll try it and post up the results. Thanks for your input. 


Oli.

---

