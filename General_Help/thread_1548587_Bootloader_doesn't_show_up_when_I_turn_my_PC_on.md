---
title: "Bootloader doesn't show up when I turn my PC on?"
date: 2010-08-08
forum: General Help
---

### Post by ryanyehh on 2010-08-08
Sorry if this is a stupid question and can be easily fixed, but after several googles I cannot find the reason why the bootloader won't show up when I turn on the PC. The only things that come up with search results are 'Why ubuntu isn't on the boatloader' but my problem is is that the boot loader doesn't even SHOW UP.

Installation went completely fine, downloaded a version 10 32-bit iso file and then put in the folder with wibu and it asked me to restart. Restarted the PC, nothing came up so I thought you might have to restart again, restarted again, still no bootloader.

After looking in the 'Add/Remove Programs' of Windows it does say it's installed, so why the bootloader isn't showing up is rather mindbobbling.

Any ideas? Thanks.

(I've been up pretty much for 2 days sorting out my PC and stuff so forgive me if anything sounds a bit, 'weird')

---

### Post by ryanyehh on 2010-08-08
Sorry for the double post, didn't know any other way to report that this was solved now.

For anyone who views this with the 'Search' and has the same problem as me, all I did was go into normal Windows bootloader set up and instead of it giving me 1 second to choose an OS (1 second? wtf, what kind of default option is that) I obviously changed it to something more suitable, like 15 seconds. 

Then after that choose Ubuntu, finish the installation and then update everything on Ubuntu and it will install the GRUB bootloader. (For some reason it didn't install with wibu)

---

