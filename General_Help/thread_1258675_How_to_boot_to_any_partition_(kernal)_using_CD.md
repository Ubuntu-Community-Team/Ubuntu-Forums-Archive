---
title: "How to boot to any partition (kernal) using CD"
date: 2009-09-05
forum: General Help
---

### Post by rocknrollmouse on 2009-09-05
Hi

I've heard its possible to boot to any hard drive, or kernal, using a CD.  
(There must be a "how to" somewhere, but I can't find it!)

Can anyone explain how to do this?

Also, can I use my server *Install* CD, or do I need a *Live* or *Alternate* disk to do this?


Many thanks.

---

### Post by rocknrollmouse on 2009-09-06
Progress (almost):
Here is a similar article for RedHat / Mandrake:
   [Solving Boot Problems with Grub]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/9398-solving-boot-problems-grub-2nd-edition.html")

Unfortunately the boot options for these distros don't relate to the Ubuntu ones, so I still don't know how to get to the grub prompt from an Ubuntu CD.

Any ideas anyone?

---

### Post by hal8000 on 2009-09-06
> **rocknrollmouse said:**
> Progress (almost):

Unfortunately the boot options for these distros don't relate to the Ubuntu ones, so I still don't know how to get to the grub prompt from an Ubuntu CD.

Any ideas anyone?

From the ubuntu live CD, applications, accesories, terminal.

---

### Post by hal8000 on 2009-09-06
> **rocknrollmouse said:**
> Hi

I've heard its possible to boot to any hard drive, or kernal, using a CD.  
(There must be a "how to" somewhere, but I can't find it!)

Can anyone explain how to do this?

Also, can I use my server *Install* CD, or do I need a *Live* or *Alternate* disk to do this?


Many thanks.


If you want to boot another OS from grub, then its a matter of adding lines
 to /boot/grub/menu.lst to create a new stanza

If you want to boot direct from grub, then you need to first open a terminal and get to a grub shell then follow

[http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html)

---

### Post by mike555 on 2009-09-06
you could use the bootmanager "Plop" from ...
[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)    , in the download is a live  .iso that you burn to cd that lets you use to boot most any system without installing ....... there is also in the download an install .iso version .. make sure you use the one you want ...

---

### Post by rocknrollmouse on 2009-09-06
> **hal8000 said:**
> If you want to boot another OS from grub, then its a matter of adding lines
 to /boot/grub/menu.lst to create a new stanza

If you want to boot direct from grub, then you need to first open a terminal and get to a grub shell then follow

[http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_4.html)

No I'm just considering Linux, specifically Ubuntu server, at the moment.  (Although I though it a useful skill to know.)

Yes I'm just trying to use the CD to boot the installed OS.
To open a terminal in a live session, haven't I already booted from the CD - in which case how do I transfer control from Live to the installed?

Thanks for the help page, some good walk through on starting other OSs.

> **mike555 said:**
> you could use the bootmanager "Plop" from ...
[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html) 
Thanks Mike, I'll have a look - especially as it looks like it should also deal with my next complication - the machine that started all this runs mirrored disks, and I want to be able to boot from either drive.

---

