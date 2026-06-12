---
title: "flash player doesn't work anymore"
date: 2009-08-17
forum: General Help
---

### Post by cedric_libre on 2009-08-17
Hi,
I am not used to going on youtube as video quality is crap IMHA .
Anyway, a few days ago, as I was looking for a DIY video about wall painting , I landed on youtube .
I saw a video, and at the end of it, that I hardly saw, as I got the initial and final pictures of, I have been advised to download adobe flash player, or perhaps to upgrade, I don't remember very precisely.
Anyway, I followed this advice and downloaded a .deb file .
The Ubuntu 8.04 package installer warned me that this package was older than the one in the repositories, and advised me not to install this one.
So I interrupted the first install process, and decided to install the adobe-flashplugin package from the repositories .
I did it, and from then I haven'y been able to see a flash video, even very hashed, as on youtube, the first picture of every video don't show up anymore.
I have checked using synaptic that the package was installed, and it seems ok, but loading the aboutlugins url in firefox, I saw that the flash player is not registered .

I tried to remove and reinstall adobe-flashplugin without success for viewing flash video .
I am using Ubuntu Hardy 8.04 .

Is there something else to do than trying to reinstall firefox ?

Thanks a lot for your help

---

### Post by Post Monkeh on 2009-08-17
put this in a terminal

```
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-nonfree
```

---

### Post by cedric_libre on 2009-08-24
Yes :-)
 You found the clue, it works now .
 Thanks very much man !
 Bye,
 Cédric

---

