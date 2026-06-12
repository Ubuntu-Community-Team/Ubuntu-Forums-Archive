---
title: "Won't wake up from hibernate - only Memtest option"
date: 2009-11-02
forum: General Help
---

### Post by pixelot on 2009-11-02
Pretty simple. I hibernated in Ubuntu 9.10, and it shut off. When I hit the power button, GRUB came up with only Ubuntu 9.10 +memtest as an option (and Windows XP, since I have that installed). I tried both, and Windows booted, and Memtest ran, but I can't get back to Ubuntu.

Any suggestions?

---

### Post by ALLurGroceries on 2009-11-02
Can you try booting off of the CD in rescue mode and reinstall grub? It sounds like your grub config is missing your new kernel from the upgrade.

---

### Post by pixelot on 2009-11-02
> **ALLurGroceries said:**
> Can you try booting off of the CD in rescue mode and reinstall grub? It sounds like your grub config is missing your new kernel from the upgrade.

Thanks for the reply. I tried booting from the Live CD, but it said there was no dedicated rescue mode on the CD, but that I could use the command line to run repairs.

I did try reinstalling GRUB as per [this guide]("http://ubuntuforums.org/showthread.php?t=224351"), but it still doesn't show the other boot options.

So maybe I'll just reinstall... but hopefully I can recover some of my profile. :rolleyes:

---

### Post by ALLurGroceries on 2009-11-02
What about plain old **grub-install /dev/hdX**?

---

### Post by pixelot on 2009-11-02
> **ALLurGroceries said:**
> What about plain old **grub-install /dev/hdX**?

I will try that. So if my results for *fdisk -l* show my Ubuntu partition as *sda5*, I would run *grub-install /dev/sda5*?

Thanks.

---

### Post by ALLurGroceries on 2009-11-02
Only if sda5 is a boot partition.. you probably want to install to the MBR of the device so just plain **grub-install /dev/sda** is probably what you should do.

---

### Post by pixelot on 2009-11-02
I tried that, with no results. sda, hda, etc. came back with an error message. So I reinstalled, and it's all good.

Thanks!

---

