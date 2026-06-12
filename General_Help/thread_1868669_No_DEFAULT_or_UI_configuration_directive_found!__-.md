---
title: "No DEFAULT or UI configuration directive found!  -Cannot install"
date: 2011-10-24
forum: General Help
---

### Post by Landsharkk on 2011-10-24
I downloaded the ISO from ubuntu and burned it to a cd.  When booting up with the cd I get the message:


**No DEFAULT or UI configuration directive found!**


I've read that some people got around this by renaming isolinux.bin to syslinux.bin and isolinux.cfg to syslinux.cfg and also by moving the isolinux folder into the 'boot' folder.

I don't have a way of editing the iso and my real concern here, is that I decided to choose Ubuntu to run my file/media share over the previous windows install.  So far my first experience with Ubuntu tells me I've made the wrong choice.  Why should the official ISO image from ubuntu need to be edited in order for it to work?

---

### Post by jsouther on 2012-02-13
Worked on this all day and I corrected my problem by changing my BIOS from SATA **AHCI Mode** back to **IDE** **Mode**.

---

