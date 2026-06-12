---
title: "Boot from SD Card help"
date: 2011-09-05
forum: General Help
---

### Post by barcode7 on 2011-09-05
Hello guys I have a notebook Acer aspire 5520 and I installed xubuntu on a 16gb SD Card but it wont boot from it. Is there any chance i can make this work?i dont have a hard drive for this machine and I really need it to boot from this SD Card. any help will be appreciated and thanks in advance.

---

### Post by searchfgold6789 on 2011-09-05
Repeatedly tap F12 as the computer boots to get a boot menu. (I think it is F12 - last time I checked with the Aspires - but it may be different.) Try booting from USB if the card isn't listed, and it may take a couple of reboots.
Otherwise, you'll probably have to buy an SD-card-to-USB adapter.

---

### Post by barcode7 on 2011-09-06
I tried that but it wont boot, any other suggestions please?really need this to work.is there any way to make a bootloader and make it load from there or something similar?like PLOP

---

### Post by barcode7 on 2011-09-06
aaanyoneee??

---

### Post by Mark Phelps on 2011-09-06
One thing you could check out is that, in some cases, an inserted memory card is treated by the PC BIOS as a "B" drive -- yeah I know that sounds crazy, but I've run into this myself.

So, next time you boot, look in the BIOS to see if it sees a "B" drive -- and try booting from that.

Also, you said you installed to the SD card.  Could be that the installation is bad.  So, instead of that, grab another PC and use Unetbootin to create a bootable version of Unix on that card -- and see if THAT boots.  IF it does, and Xubuntu did not, then your Xubuntu install bad.

---

### Post by barcode7 on 2011-09-06
thank you for your suggestions Mark but nothing worked, I tried all that you said.. i guess this laptop doesnt want to boot from an sd card. thank you for your time tho any more suggestions are welcomed

---

