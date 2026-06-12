---
title: "Running text console at 1920x1200 or x1080"
date: 2009-12-21
forum: General Help
---

### Post by Zenith88 on 2009-12-21
There are several write-ups on the Net about that, for example this one:

[http://community.spiceworks.com/how_to/show/54](http://community.spiceworks.com/how_to/show/54)

Some of them are outdated, but other are relatively new, and all of them use the same steps to achieving a high res console:

1. grub menu resolution in /etc/default/grub, I've done it.
2. splash screen resolution I forgot where, I've done it too.
3. VESA console resolution in kernel vga parameter. I've tried it.

The 3d is problematic, as the kernel in Ubuntu 9.10 does not like any vga options at all.
vga=ask, vga=0x101, vga=0x346 and vga=795 all result in an error message from the kernel:

vga=xxx option is deprecated

So it is a kernel problem and not grub problem as someone suggested in #ubuntu IRC channel last night.

Sometimes I need to boot into text only mode and having 80x25 is a major PITA.

Any ideas welcome.

---

### Post by pbrane on 2009-12-21
Actually the vga=xxx being deprecated is a grub2 issue. I still use the vga=xxx in /etc/default/grub because the other options I've found don't work. I just ignore the warning message from grub. 

The idea is to use gfxpayload=XRESxYRES. You can add that to /etc/default/grub. However that won't work without vesafb and that is blacklisted in Ubuntu. Also I found that enabling it causes a black screen, i.e., no console at all. I went on #grub channel in IRC to try to get this to work, they were great but I can't get it to work. I did the same thing that's in your example. Plus edited /etc/grub.d/00_header and added the needed stuff. Nothing seemed to work. Either the resolution didn't change or I got a black screen, no cursor, or just a flashing cursor.

So if I were you I'd use the vga=xxx option until someone finds a better way in Ubuntu.

---

### Post by Zenith88 on 2009-12-21
> **pbrane said:**
> So if I were you I'd use the vga=xxx option until someone finds a better way in Ubuntu.

Let me get it straight: are you suggesting that vga=xxx actually works, what I thought was an error is actually a warning, and console should change to the given mode? But the last part does not happen, regardless of the vga=xxx option I still see the same ugly 80x25 screen in 640x480x16.

The funniest part is that grub command vbeinfo does not even list the modes such as 1920x1200 that I used under Fedora 11-12 with any kernel.

Just tried again, and instead of switching to 0x346, which is 1920x1200, iw switched into 320x200.

I am baffled, as this is the same 2.6.31 kernel which I ran under Fedora and CentOS just a few weeks ago. Has someone patched the kernel for Karmic Koala to prevent normal vga parameter handling or am I completely misunderstanding the divine gift I am getting?

---

### Post by pbrane on 2009-12-22
I am running Karmic and yes **vga=791** works for me. 1024x768 is an okay resolution for a terminal, at least for me. My laptop panel is 1440x900 native. You have to make sure that the mode you choose is supported. If they aren't listed by vbeinfo they won't work. Also vbe and vga mode numbers are 512 ( 0x200 in hex ) apart. I think vga is the higher one.

What I see when I boot is grub saying something about 'vga=xxx is deprecated, use gfxpayload instead' for about 2 seconds. Then it continues.

Also make sure you run **update-grub2** after you edit /etc/default/grub.

Of course all this assumes you are using grub2 and not legacy grub.

---

### Post by Zenith88 on 2009-12-22
> **pbrane said:**
> I am running Karmic and yes **vga=791** works for me. 1024x768 is an okay resolution for a terminal, at least for me. My laptop panel is 1440x900 native.
I think that's the key. My display is 1920x1200 and the modes displayed by vbeinfo are cut off at 1600x1200. Your 1440x900 mode is there, my mode is not.

My mode was supported by the same version of kernel under Fedora 11, 12 and CentOS 5.4, so it's becoming painfully obvious that kernel is patched. Using the same kernel under a different distro allowed me to switch console resolution with no effort at all.

---

### Post by pbrane on 2009-12-23
So your display is 1920x1200 native? What vbeinfo is reporting should be what is supported by your BIOS. But may it's a bug. And yes, the ubuntu kernel has different options enabled and patches than the fedora kernel. But for the most part they are very similar.

I think though that grub2 is what reads the BIOS and displays it when you type 'vbeinfo', mainly because the kernel hasn't been booted yet.

I'm not sure where to go with this one. Can you use 1920x1200 in GNOME or KDE or whatever desktop you use? When I think about it I'm not sure if I ever got 1440x900 to work as a **vga=xxx** kernel parameter. Not sure if I even tried. But I will and report back.

---

### Post by Zenith88 on 2009-12-31
> **pbrane said:**
> So your display is 1920x1200 native? What vbeinfo is reporting should be what is supported by your BIOS. 

Then I have a question: why this change to the worse? If using the same kernel under different distro I could get 1920x1200 console using vga=0x346 parameter, why should I be confined to a non-native resolution under Ubuntu? This is the same kernel, I repeat!

Needless to say that graphic front page of grub2 is using some ridiculously slow algorithm to draw - issuing vbeinfo command starts scrolling the page and I can literally see each pixel being drawn. It takes forever to wait until all lines finish scrolling.

My god, how do people manage to screw things up to total SNAFU???

---

### Post by Zenith88 on 2010-01-05
Tried adding gfxpayload option to /etc/default/grub as this:

gfxpayload=1920x1200x16

It did not change anything, still getting 80x25 console.

---

### Post by SecretCode on 2010-01-05
Try using the vga= parameter (and ignoring gfxpayload), but also changing *linux* to *linux16* and *initrd* to *initrd16* in the grub menuentry (either by editing grub.cfg directly or editing /etc/grub.d/10_linux and rerunning update-grub).

---

### Post by Zenith88 on 2010-01-07
> **SecretCode said:**
> Try using the vga= parameter (and ignoring gfxpayload), but also changing *linux* to *linux16* and *initrd* to *initrd16* in the grub menuentry (either by editing grub.cfg directly or editing /etc/grub.d/10_linux and rerunning update-grub).

Will try that. It is sounding more and more like grub2 project has bitten more than it could swallow. :(

Edit:

linux16/initrd16 actually worked fine, all of a sudden vga=0x346 works again.

---

