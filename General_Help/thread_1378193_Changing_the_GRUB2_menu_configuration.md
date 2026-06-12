---
title: "Changing the GRUB2 menu configuration"
date: 2010-01-11
forum: General Help
---

### Post by MagPie&gt;.&lt; on 2010-01-11
Hi All,

I have just done an upgrade to my PC hardware which has allowed me to move to x64 (wehay!). I am a musician so have also installed Ubuntu Studio 9.10 on one side of my first HDD. This is all good and is all working fine, however when I boot now I have a lot of choices for GRUB2 (the BETA installed by Karmic). For example:

> Ubuntu, Linux (*******-31-17.generic)
Ubuntu, Linux (********-9-r)
Ubuntu, Linux (********-31-16.generic)
etc

I have taken a look at the configuration of my disc's, which I have listed below. What I want to do is match the options in GRUB so that I can see which OS I am loading properly, without guessing by Kernal Variation:

> Ubuntu 9.10 x64
Ubuntu Studio 9.10 x64
Ubuntu 9.10 x86
Ubuntu 9.10 x86 (recovery mode)
Memtest86+
Windows XP x86

I have read the article on this and creating custom menu items, but my problem is I don't want to append the menu items- I want a single menu without the various Kernals given which is clean and clearly labelled. The article and indeed the grub.cfg said that I shouldn't directly edit the config, but I am not sure of any other ways to make this change.

Also, is it possible to remove old /boot areas from an partion install? It would be nice to have one single boot partion rather than the three boot areas provided by each subsequent install.

Many Thanks,


MagPie>.<

---

