---
title: "Bootloader on USB drive, OS on SD card"
date: 2012-06-01
forum: General Help
---

### Post by blackflame2996 on 2012-06-01
I have a Dell Inspiron 14r, and would like to boot Ubuntu from a 32 GB SDHC C4 card I have. However, the 14r does not support booting from the internal card reader. Is it possible to install the bootloader to a USB drive, and have the system on the card?

---

### Post by carl4926 on 2012-06-01
Assuming the machine supports USB booting
You have the USB as the 1st boot device 
And write the bootloader to the USB during installation

Yes it should work, I think. I never tried it.

---

### Post by blackflame2996 on 2012-06-02
when I tried this last night, GRUB just poped up saying 
> error: no such device
GRUB Rescue>
Any suggestions?

---

### Post by carl4926 on 2012-06-02
> **blackflame2996 said:**
> when I tried this last night, GRUB just poped up saying 

Any suggestions?
Not really
I'd have to experiment myself as I haven't done this before, but it's just time to mess with it. And I don't have your exact setup either.

This may be the sticking point
> a 32 GB SDHC C4 card I have. However, the 14r does not support booting from the internal card readerBecause this device may not work sufficiently so early on in the boot process.

---

### Post by blackflame2996 on 2012-06-03
I have it working by placing the entire /boot on the USB stick. I still wish I could find a way to be able to remove the stick after booting.

---

### Post by wilee-nilee on 2012-06-03
> **blackflame2996 said:**
> I have it working by placing the entire /boot on the USB stick. I still wish I could find a way to be able to remove the stick after booting.

I suspect the internal card would work, but you are just not getting there.

You can just use supergrub on a stick if needed, it will allow removal upon boot, and will boot multiple installs.

[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

Does the internal card show in the bios as a seperate entity, like a HD, or a usb?

---

### Post by blackflame2996 on 2012-06-04
The BIOS doesen't show up at all in the BIOS. I just tried Super GRUB2, it didn't find the sd card.

---

### Post by wilee-nilee on 2012-06-04
> **blackflame2996 said:**
> The BIOS doesen't show up at all in the BIOS. I just tried Super GRUB2, it didn't find the sd card.

If you have actually installed to the card run the bootscript and post it to the thread.

Download the link in ubuntu or a ubuntu live cd, extract it to the desktop, and run the command, copy and paste all the text from the results.txt to a reply.

When you paste if highlight all that text and click on the # in the reply panel to wrap it in code tags.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

