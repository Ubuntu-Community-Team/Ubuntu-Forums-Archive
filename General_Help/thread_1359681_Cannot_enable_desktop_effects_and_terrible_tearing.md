---
title: "Cannot enable desktop effects and terrible tearing in flash!"
date: 2009-12-20
forum: General Help
---

### Post by mwgriffin on 2009-12-20
I just installed Ubuntu 9.10 and updated everything as well as installed a new nVidia 8400 gs.  I cannot enable desktop effects.  When I try even "normal" effects it says "cannot enable desktop effects."  Also when viewing flash movies the tearing is horrible compared to the integrated intel card.  This is an old computer so the integrated card is terrible and the upgrade to an 8400 gs with 512 mb of ram should be significant.  But I activated the drivers (version 185) through the hardware drivers dialogue box, but desktop effects doesn't work, and the performance is worse than with the integrated card...  What can I do?  Thanks!!!

---

### Post by Dark_Stang on 2009-12-20
What kind of power supply are you running?

---

### Post by mwgriffin on 2009-12-20
I have no clue, but I can tell that the card is functioning as before installing the graphics card drivers, the vertical refresh of just the windows could be seen if they were dragged around.  It took for ever.

---

### Post by Dark_Stang on 2009-12-20
Well, with an 8400 I'd recommend running a 400w or higher power supply. You could probably get away with a 350w, but I wouldn't go any lower. But that would be the first thing I'd look into.

---

### Post by starfunker on 2009-12-20
> **mwgriffin said:**
> I just installed Ubuntu 9.10 and updated everything as well as installed a new nVidia 8400 gs.  I cannot enable desktop effects.  When I try even "normal" effects it says "cannot enable desktop effects."  Also when viewing flash movies the tearing is horrible compared to the integrated intel card.  This is an old computer so the integrated card is terrible and the upgrade to an 8400 gs with 512 mb of ram should be significant.  But I activated the drivers (version 185) through the hardware drivers dialogue box, but desktop effects doesn't work, and the performance is worse than with the integrated card...  What can I do?  Thanks!!!

I'm having terrible flash performance as well.  I have an 8800gt graphics card that has worked previously with Ubuntu, but watching iplayer or youtube becomes unbearable after about five minutes as the picture tears and becomes little more than a series of static pictures while the sounds continues without a problem.

I have tried using both Adobe flash and the non-free flashplugin from Synaptic.

---

### Post by starfunker on 2009-12-20
well, I think I've fixed it.  I'd been having problems for a while, as it seemed that I wasn't getting the performance from my graphics card that I should.  I took a guess that it might be something to do with using 32 bit on a system that can use 64bit (despite only having 2 gigs of RAM).

Installed the 64bit version, followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=1358591") to install 64bit flash, and then followed [this]("http://astoryworthtelling.wordpress.com/2009/11/09/cant-click-in-flash-using-ubuntu-9-10-karmic-try-this/") to fix a small problem with being unable to click on anything in flash.  Now I have much improved graphics all round, flash works and I couldn't be happier. Just strange that it requires the 64 bit version when I shouldn't get any performance boost from it with such little RAM.

---

