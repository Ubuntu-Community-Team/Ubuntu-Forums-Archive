---
title: "how to change screen rez thats displayed BEFORE the gdm login?"
date: 2012-08-21
forum: General Help
---

### Post by ferrisxb9r on 2012-08-21
Recently installed 12.04 LTS x64 dual booting with Win7 on a Clevo Horize P170HM SE laptop (native screen resolution is 1920x1080).  Everything is pretty hunky dorey, had a few issues getting the Nvidia GTX580M working nicely out of the box (had to install the restricted drivers before it would work out of safe graphics mode).

With a quite a few Ubuntu installs under my belt over the years, this is the 1st time I've had this particular issue.

You know as you're booting, and you get the purple screen, and or the black screen with the DOS-like text scrolling up?  NORMALLY this is all displayed in whatever screen I'm ons native resolution.  I've never had to tweak this, it's always JUST WORKED.

With this laptop though, for the 1st time ever, it's all displayed at... 640x480?  800x600?  I'm not entirely sure, it's just a very low rez.

Now I'm only niggling, as it doesn't prevent any functional issues, and as soon as the GDM login screen appears everything is displayed in 1920x1080 as it should be.  But I'd really like to adjust the settings to change this pre-login screen rez to my native rez, to keep it uniform across the board.

I'm quite adept at USING the CLI, and have no problems following instructions, but I don't stay abreast of all the changes with the different releases of Ubuntu, and I'm unsure if I need to be changing a xorg.conf (which currently doesn't seem to exist on my 12.04 install) or something else these days.

Can someone please point me in the right direction as to either what file I need to tweak, or which command I will need to run to alter this pre-login screen resolution?  Is it something to do with xrandr?

Any help at all would be much appreciated.

---

### Post by dcstar on 2012-08-23
> **ferrisxb9r said:**
> 
.........
Can someone please point me in the right direction as to either what file I need to tweak, or which command I will need to run to alter this pre-login screen resolution?  Is it something to do with xrandr?

Any help at all would be much appreciated.

You edit the Grub defaults file and manually set the VESA resolution - do a web search as there are multiple sites with detailed instructions.

---

### Post by ferrisxb9r on 2012-08-23
> **dcstar said:**
> You edit the Grub defaults file and manually set the VESA resolution - do a web search as there are multiple sites with detailed instructions.

Actually, I was told this instead

> Short answer, I don't think it's possible.

The problem in this case is related to the nvidia card/binary driver and it's lack of KMS (Kernel ModeSetting) support, and the way plymouth (ubuntu splash screen controller) works. 

Someone who can explain it better than me:
[http://netsplit.com/2010/03/30/all-a...-mode-setting/](http://netsplit.com/2010/03/30/all-a...-mode-setting/)

and

> Correct - not possible for the KMS reasons above. 

Nvidia have only just gotten around to supporting XRandR this year, despite the feature existing since 2001. That's pretty awful turn around.

Linus Torvalds (original author, and head of the Linux kernel project) criticised Nvidia heavily quite recently about how they interact with the open source community, and these sorts of problems are classic examples of what he's talking about.

The choices as an Nvidia user are either use the binary drivers and suffer ugly mode settings on boot, or attempt to use the open source Nouveau drivers which have poor support for many cards and are quite buggy, thanks to a complete lack of documentation from Nvidia.

If you have the option, ATI and Intel video cards have much better driver support under Linux, as both companies offer open source drivers as part of the Xorg and Linux Kernel projects, which support all of the KMS, XRandR, OpenGL and other features you'd expect out of the box.

---

### Post by zombifier25 on 2012-08-23
I use an NVIDIA driver, and this worked:
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)
works on newer versions.

---

