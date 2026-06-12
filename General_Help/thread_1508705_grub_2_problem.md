---
title: "grub 2 problem"
date: 2010-06-13
forum: General Help
---

### Post by PerryCarvish on 2010-06-13
My question concerns grub2 and updating to ubuntu 10.04. I am running a dual boot with windows 7 and ubuntu 9.10. I have a separate 160 gig hard drive for ubuntu and a 60 gig ssd for windows. because my windows was in 64 bit I thought I should do the same with ubuntu, however I was wrong, the 32 bit version seems more stable. I tried to burn a iso of 10.04 32 bit but it wouldn't install ( error Messages) So I installed my 9.10 version and I will just update to version 10.04. My question, do I have to update the grub loader to version 2 or can I just keep my version 1 ? Every time I update the grub to version 2, my bios crashes and I get the error message "grub_puts_" not found. then I have to revert back to version 9.10 which means uninstalling ubuntu booting into windows , reseting my loader to the vista loader with easy bcd. I've done this several times now, with 64 bit and 32, I just thought if I don't have to update grub, then the loader won't crash. Or is there an alternative to the grub 2 ?

---

### Post by quixote on 2010-06-15
Yes, the old grub is called grub-legacy and instructions on reverting to it are [here]("https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy").  That page also has detailed info on how to recover from all sorts of grub2 errors.  The equivalent for old-grub is [here]("https://help.ubuntu.com/community/GrubHowto").  

Sorry to hear this has been giving you so much grief!

---

