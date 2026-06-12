---
title: "ubuntu and fedora15"
date: 2011-07-04
forum: General Help
---

### Post by rbrick49 on 2011-07-04
Hi folks can someone help me out here please,I have 4 sata hard drives in my box sda,ubuntu natty sdb,ubuntu oneiric sdc,kubuntu oneiric sdd,vacant I have tried to install fedora 15 on sdd it loads but stops the others from booting can someone help me out please in plain english as I am old and the brain dont work to flash these day
regards Ronnie

---

### Post by decrepit on 2011-07-04
My last fedora was #12. In that, unlike ubuntu, you had to add your other OSs to grub manually. I'm not sure if fedora has gone to grub2 or not, the method for manual editing is different, in each

I'd recomend posting on a fedora forum, try 
[http://www.linuxquestions.org/questions/fedora-35/](http://www.linuxquestions.org/questions/fedora-35/)

they should be able to help.

---

### Post by nothingspecial on 2011-07-04
The easiest way to dual boot Ubuntu and Fedora is to install Fedora first.

Fedora uses legacy grub which means you have to manually add Ubuntu to the boot menu.

Ubuntu will detect Fedora and add it to the boot menu when you install it.

Another tip, if you wish to share data between the 2 distros easily. When you install fedora, manually specify your uid and gid which in Ubuntu default to 1000:1000, that way you don't run into any permission issues.

---

### Post by beew on 2011-07-04
> **rbrick49 said:**
> Hi folks can someone help me out here please,I have 4 sata hard drives in my box sda,ubuntu natty sdb,ubuntu oneiric sdc,kubuntu oneiric sdd,vacant I have tried to install fedora 15 on sdd it loads but stops the others from booting can someone help me out please in plain english as I am old and the brain dont work to flash these day
regards Ronnie

When you installed Fedora you should have chosen not to install the bootloader.

---

### Post by beew on 2011-07-04
> **nothingspecial said:**
> The easiest way to dual boot Ubuntu and Fedora is to install Fedora first.

Fedora uses legacy grub which means you have to manually add Ubuntu to the boot menu.

Ubuntu will detect Fedora and add it to the boot menu when you install it.

Another tip, if you wish to share data between the 2 distros easily. When you install fedora, manually specify your uid and gid which in Ubuntu default to 1000:1000, that way you don't run into any permission issues.

No, it is a easier to install Ubuntu first. Then install Fedora without installing the bootloader and then log in to Ubuntu and run "sudo update-grub" and grub2 will find Fedora and add it to the boot menu.

---

### Post by nothingspecial on 2011-07-04
> **beew said:**
> No, it is a lot easier to install Ubuntu first. Then install Fedora without installing the bootloader and then log in to Ubuntu and run "sudo update-grub" and grub2 will find Fedora and add it to the boot menu. With grub2 you don't need to do all these manual stuffs.

I'd say the both accomplish the same thing.

---

### Post by rbrick49 on 2011-07-05
I had to install fedora on sda then put boot loader in first sector of boot partition then install ubuntu on sdd then update-grub all is good now all four distros booting fine
thanks folks for the input

---

