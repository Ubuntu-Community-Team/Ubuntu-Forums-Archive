---
title: "Sapphire X800gto2 causes nothing but problems with any distro of Linux, what to do?"
date: 2006-04-15
forum: General Help
---

### Post by Thasp on 2006-04-15
I get X errors about seeing no display advice when booting up ubuntu livecds, kubuntu live cds, and general errors/freezes when using any distro of linux(suse, ubuntu, kubuntu too) with this card.

However with my X300se I have no issues. Stuff works fine. In addition, 1/4 of the time I go into my mobo bios with this card, the screen gets a bunch of purple and blue lines on it, so I have to reboot since that is all I see with a black screen behind it, and try to go into the BIOS again. This doesn't happen with the X300se either. 

What should I do to fix this? If needed, I can tell the specific errors. I RMAd the card because of this issue but the new one has the same issue. This is my second card, and a different revision than the first one with a different chip. This is the R430, instead of the better R480, but both have the same problems. I don't want to be stuck with an x300se, that'd be a dealbreaker back into using windows since I am not going to dump a card that works 100% fine in windows, that can play games overclocked without artifacts for hours at a time no problem just because it does not work with linux.

Any advice or insight into fixing this issue would be appreciated. Sapphire's tech support doesn't speak english at a higher than 3rd grade level, or even respond half the time so I don't bother with them anymore. It took them five weeks just to get the new card to me from the time I asked for an RMA number.

---

### Post by Thasp on 2006-04-16
bump

---

### Post by Thasp on 2006-04-17
Ok I fixed it by doing sudo nano /etc/X11/xorg.conf and changing the ATI driver to a vesa driver. I have very little time on my hands lately to tweak linux, but getting it working on my new hardware was a critical step. I searched here and after looking through many posts with irrevalent information, found one with relevant information. :)

[http://ubuntuforums.org/showpost.php?p=889687&postcount=4](http://ubuntuforums.org/showpost.php?p=889687&postcount=4) was it

---

