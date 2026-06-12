---
title: "hp lh pro which video"
date: 2006-02-05
forum: General Help
---

### Post by jrjerry on 2006-02-05
trying to find out which video driver the lh pro uses in the standard setup-thanks for your help

---

### Post by jrjerry on 2006-02-06
i think it uses the trident 9000 drivers but when i select that xserver wont load--any ideas on what to try-

---

### Post by RAOF on 2006-02-06
You could try running "lspci" from a console - that will list all the PCI devices & give some basic information about them.  One of them may be your graphics card, and that'll help you find the right driver.

---

### Post by jrjerry on 2006-02-07
i was trying to use the onboard video-i think i will have to invest in a pci vieo card to get it to load.i was trying to avoid that because after i get it set up i won't even need a moniter-any recomendatoins on a cheap pci card that will get recognized  thanks

---

### Post by RAOF on 2006-02-07
The onboard video will probably be connected to the PCI bus, and so will show up in the output of "lspci".  Could you try running it & posting the output here?  I'll see if I can work out what card it is :)

---

### Post by jrjerry on 2006-02-08
i will try to run Ispci tonight and see what i get  thanks

---

### Post by jrjerry on 2006-02-08
ran lspci all that showed up was my raid card my ethernet card and my modem-i'm trying to run the live cd--just to make sure it will work on this system before i load it.it is a hp netserver lh pro-has dual pentium pro 200 processors 2 4g &3 9g scsci hard drives-what i wanted to do wasset it up as a server for my home network and learn linux while doing it .all i can say is it has been interesting so far but i am very patient and appreciate any help i can get

---

### Post by jrjerry on 2006-03-07
bought a cheap pci video card so i am up and running now-i'm trying to get my raid straighten out and i don't have any sound-i haven't had this much fun since dos

---

