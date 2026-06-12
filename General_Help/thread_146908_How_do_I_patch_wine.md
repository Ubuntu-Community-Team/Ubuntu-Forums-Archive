---
title: "How do I patch wine?"
date: 2006-03-19
forum: General Help
---

### Post by Ubuntufan06 on 2006-03-19
I found a homepage with some patches for the DirectDraw in Wine. I play a game name Tibia, and it gives me alot of errors when loading, something about ddraw. Then, the graphic ingame is really bad since Wine can't show any light effects.

Anyhow, this guy seems to have managed to fix the ddraw in wine, but how do I patch it?
[http://stud4.tuwien.ac.at/~e0526822/](http://stud4.tuwien.ac.at/~e0526822/)

He gives 2 files to download, but since I'm kind of new to this whole linux thing, I will need lots of help. I don't even know what CVS is and how it works.

All I've done is to install apps and games with sudo apt-get install, so a nice guide on how to apply and install this patch with the latest wine would be very nice :)

I'm running Kubuntu Breezy 5.10.

---

### Post by dermotti on 2006-03-19
Im not new to linux, and cvs still is tought for me :-/

---

### Post by Ubuntufan06 on 2006-03-19
@dermotti: Tought, but now new? Maybe you could help me out then :P

---

### Post by patbuntu on 2006-03-19
cvs is a version control system commonly used to keep track of changes to source files.  Download the latest wine cvs by following the instructions on:

[http://www.winehq.com/site/cvs](http://www.winehq.com/site/cvs)

This wil basically get you all the latest source code for wine. You'll then have to build it yourself.  Instructions for this are here:

[http://www.winehq.com/site/docs/wine-faq/index#HOW-DO-I-COMPILE-THE-WINE-SOURCE-CODE](http://www.winehq.com/site/docs/wine-faq/index#HOW-DO-I-COMPILE-THE-WINE-SOURCE-CODE)

You may not have all the dev tools required to do this bit, but if you have a look in the programming / development section on this forum you should be able to find the packages you need and get them from synaptic.

Once you've got it building and running, you need to get this guys patch and apply it to your wine source tree.  This will update a couple of files with his changes.  Then rebuild everything again and you should be happy, assuming that:

a) This patch works and doesn't break the build process
b) The patch actually does what you want, and works with your game

I've never tried this BTW, but I think this is the general process you need to follow

hope this helps

-Pat

---

