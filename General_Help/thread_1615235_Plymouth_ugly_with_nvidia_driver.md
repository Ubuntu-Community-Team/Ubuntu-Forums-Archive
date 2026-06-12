---
title: "Plymouth ugly with nvidia driver"
date: 2010-11-06
forum: General Help
---

### Post by gufide on 2010-11-06
I recently buy a 1366x768 laptop with nvidia gts 360m (asus  G60Jx-rbbx05). I installed the nvidia driver version 256.53 for  compatibility issue and now work great. I followed multiple tutorial to  fix the very ugly plymouth boot, but no one support 1366x768, and only  support 1024x768. Can I get a normal plymouth with the nvidia driver?

---

### Post by Aydos on 2010-11-12
I really hope a solution comes up for this.

I game and run alot of Windows games via WINE on my gaming rig.

It is a beast of a machine and alot of time the wine site recommends running the latest official nvidia drivers from their site to get a game running properly in WINE.

This leaves me with a broken ugly plymouth screen. I have tried every fix on the web. I can get it in a normal resolution, but it is still an ugly pink screen. I would love to run the most current NVIDIA drivers and keep the sleek black splash screen with the nice ubuntu logo and the dots that load up instead of this pink fiasco I have on my screen.

---

### Post by mister_playboy on 2010-11-12
Did you guys already try this?

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by sgage on 2010-11-12
That seems overly busy. Here's what I do, and it works just fine. It came from a post during Maverick testing, but I don't know who to attribute it to.

'You may use uvesafb to get a nice looking bootsplash. Just install "v86d" (universe), put something like


uvesafb mode_option=1280x1024-32@60 mtrr=3 scroll=ywrap



in /etc/initramfs-tools/modules and run


sudo update-initramfs -u


That's it - done. No messing around with grub. Just one quick mod to one file.

---

### Post by Aydos on 2010-11-12
Yes I have tried all of those. Basically, I end up with a high res ugly splash screen.

By the way, does anyone know if I could use a different resolution besides the on in the example? I run everything at 1920 X 1080 and would like it to all sync.

Why have they not just patched this lol?

---

### Post by Aydos on 2010-11-12
> **sgage said:**
> That seems overly busy. Here's what I do, and it works just fine. It came from a post during Maverick testing, but I don't know who to attribute it to.

'You may use uvesafb to get a nice looking bootsplash. Just install "v86d" (universe), put something like


uvesafb mode_option=1280x1024-32@60 mtrr=3 scroll=ywrap



in /etc/initramfs-tools/modules and run


sudo update-initramfs -u


That's it - done. No messing around with grub. Just one quick mod to one file.

Nice I will try that way.

---

