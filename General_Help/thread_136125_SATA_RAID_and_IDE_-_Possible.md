---
title: "SATA RAID and IDE - Possible?"
date: 2006-02-25
forum: General Help
---

### Post by Alex[RM-UK] on 2006-02-25
Hey, 

I am wanting to install Ubuntu again on my old hard drive, because recently I got 2 new SATA ones ( RAID 0). Here is my setup:

2xWD SATA2 RAID 0
1xMaxtor 80GB

I want to be able to install Ubuntu on my Maxtor IDE hard drive, and still keep WinXP on my RAID config. I'd also like Ubuntu to be my primary OS ( So that GRUB loads asking me if I want to load Ubunut or WinXP )

I went ahead and started to install Kubuntu 5.10 (I couldn't find my Ubuntu disc, so i'm downloading it now) but when it got to the stage 'Installing GRUB' it just hung there.

So, is it possible to do what I want?

---

### Post by dcstar on 2006-02-25
[QUOTE='Alex[RM-UK]']
......
I went ahead and started to install Kubuntu 5.10 (I couldn't find my Ubuntu disc, so i'm downloading it now) but when it got to the stage 'Installing GRUB' it just hung there.

So, is it possible to do what I want?[/QUOTE]
Grub has to install itself on the actual boot disk for your system, and I believe it needs some space in the first 1024 logical cylinders to do this.

Your existing Windows install may be preventing this from happening, or it may be because of the particular disk hardware you are using.

Try a forum search for the symptoms you are experiencing, chances are there is a solution somewhere.

---

### Post by Alex[RM-UK] on 2006-02-26
Thanks, but i'm not going to do it now. When I booted up into Windows many files were currupted (Maily Licensing info) and it means I need to Format my XP disks....not happy :( 

Ah well,

---

