---
title: "Burning Iso to a bootable USB"
date: 2009-08-17
forum: General Help
---

### Post by rugbert on 2009-08-17
Im trying to make a bootable XP install on a USB but the only thing Ive found so far will only create ubuntu USBs or only use .img files and I need to use a .iso file.

---

### Post by HermanAB on 2009-08-17
Hmm, the ISO file format and what you need for the usual USB memory stick is very different.  However, Mandriva makes dual format images that can be stored on CDs or USB sticks, so it is possible, but gawd knows how.  Try the Mandriva Wiki and Cooker forums, someone there has to know how to do what you want.

---

### Post by vinnywright on 2009-08-17
old but mabey?

[http://articles.techrepublic.com.com/5100-22_11-5928902.html](http://articles.techrepublic.com.com/5100-22_11-5928902.html)

VINNY

---

### Post by shel-hall on 2009-08-17
> **rugbert said:**
> Im trying to make a bootable XP install on a USB ... 

You need WinSetupFromUSB ... google it and you'll find both the software download (with a completely incomprehensible writeup) and a pretty good How-To written by someone else.

Bottom line ... you need a Windows PC to run it.  You make an ISO image on your disk and use WinSetupFromUSB to write that to a USB key.  

WinSetupFromUSB will also write a bootable image to a CF card in an appropriate USB adapter, and you can use the CF card in a PCMCIA adapter to boot machines like the Toshiba Portege R100 that boot from PCMCIA rather than USB.

-Shel

---

### Post by Krupski on 2009-08-18
> **rugbert said:**
> Im trying to make a bootable XP install on a USB but the only thing Ive found so far will only create ubuntu USBs or only use .img files and I need to use a .iso file.

Actually quite easy... install XP to a scrap hard drive (or install it to a partition of the same size as your USB stick).

One thing to do on the hard drive install is TURN OFF the pagefile (Control Panel / System / Advanced Tab / Settings / Advanced / Virtual Memory / Change / Click "No Paging File" / Set / OK).

When it's all installed and activated, simply use WinImage (in Windows) or dd (in Linux) to copy the image of the hard drive to the USB stick.

Be sure "boot from USB" is set in your BIOS.

That's it. Easy.

Be warned though... it will be horribly SLOW... and without a pagefile (swapfile) you can easily run out of memory to run stuff.

(If you are doing this to build a headless file server, do yourself a favor and use Linux instead!)

---

