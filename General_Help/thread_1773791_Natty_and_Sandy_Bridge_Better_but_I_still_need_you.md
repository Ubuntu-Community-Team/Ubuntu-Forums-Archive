---
title: "Natty and Sandy Bridge: Better but I still need your help"
date: 2011-06-02
forum: General Help
---

### Post by turqoisehex on 2011-06-02
First of all, congratulations on a great release! Compared to Lucid and Maverick, I'm finding Natty much more compatible with Sandy Bridge.

However, I'm still having a few challenges. I've decided to post them all together, since I believe they're all related to hardware support, primarily because I wasn't having any of them before upgrading to Sandy Bridge, and upgrading to the latest BIOS greatly to improved things (but that was before upgrading to Natty).

**The (*probably*) easy one:**
Compiz works out of the box!!... but it doesn't turn on until I reload it with Fusion Icon. How can I have it enabled on load?

**The harder ones:**
[list][*]While downloading package indexes with “sudo apt-get update”, I occasionally get “Something wicked happened resolving... (-5 - No address associated with hostname)”. I also get DNS errors from chromium. My IP is set to static, and all other computers on the network are networking normally.
[*]My network speed drops extremely low on LAN and internet, as low as 2mbps on LAN and only a few Kbps over internet. Less commonly, it stops altogether.
[*]Copying files on the same disk tops out at 5mbps (25mbps used to be normal)
[/list]
All three of these come and go without warning or obvious cause.
Digital audio (toslink fiber optic) doesn't work, regardless of hardware settings under “Sound”.

**The worst,**
And the hardest to pin down, is the kernel panics. I'm sure there's a log somewhere that will give me more information, but at the moment all I know is that it happens most frequently during the first minute of being in the session. If you can tell me where this is logged, I can post the log.

**Details:**
Natty 32-bit, Kernel is 2.6.38-8-generic-pae. Motherboard is Gigabyte H67N-USB3-B3, F5 BIOS.

Normally I would try a variety of things before posting and asking for help, but in this scenario I honestly don't know where to begin. **Any help is greatly appreciated, thanks very much.** :D

---

### Post by dozycat on 2011-06-02
I got sandy bridge too, but I use ubuntu 11.04 64 bits and my motherboard is asus.
And I don't have any of your problems.
My only problem is with the alsa audio with linuxtv sometimes sound works well sometimes it has long delay, but recording with mencoder is perfect

---

### Post by Alasjo on 2011-06-02
Like dozycat I'm also running Natty 64-bit on Asus mobo, and have not (yet) experienced the problems you describe. However, some laggy networking have occured (when I tried streaming video over Samba share).

My big problem is getting the integrated graphics to work properly. Unity looks ok but games and other graphics-intensive applications do not work as expected (freezing picture and low fps).

I am wondering whether it is a kernel upgrade that is in order or if I need to install experimental graphics drivers, like [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

I raised the question in this thread (check it out): [http://ubuntuforums.org/showthread.php?t=1666626]("http://ubuntuforums.org/showthread.php?t=1666626")

---

### Post by turqoisehex on 2011-06-02
Thanks for the replies, maybe I should try 64-bit and see if anything changes, though I'd prefer to find a solution that wouldn't need a re-install. Alasjo, using 2.6.38-8-generic-pae my graphics are working quite well.

Does anyone know where to find a log with info on the kernel panics?

---

### Post by Alasjo on 2011-06-02
> **turqoisehex said:**
> using 2.6.38-8-generic-pae my graphics are working quite well

Ok, thanks for that info. Have you tried OpenGL/3d applications using this kernel?

---

### Post by turqoisehex on 2011-06-03
> **Alasjo said:**
> Ok, thanks for that info. Have you tried OpenGL/3d applications using this kernel?

Yep, it all works well :D
I've switched to 64 bit, so far so good!

---

