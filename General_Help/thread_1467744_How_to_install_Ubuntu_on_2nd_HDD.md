---
title: "How to install Ubuntu on 2nd HDD?"
date: 2010-05-01
forum: General Help
---

### Post by Fuel90 on 2010-05-01
Sorry if this question is asked a lot, but I can't seem to find a straight answer, but I was wondering if someone could give me some directions on how to install Ubuntu on my 2nd HDD.

I have Windows 7 on my 1st HDD.

Thanks!

---

### Post by DawieS on 2010-05-01
I recommend that:
1) you unplug the power to the first hard drive, until after the installation.
2) boot from the live CD, and install Ubuntu on the second hard drive.
3) after the installation, power down, and restore the power to your first hard drive. Adjust your BIOS to boot from the second drive (Ubuntu). 

After booting up in Ubuntu, mount all drives by clicking on them in the file browser. Open a terminal, and type the following command to update the Grub menu (include Windows 7):
```
sudo update-grub
```This procedure will ensure that nothing is changed on your first drive. Also, the first drive will not be referenced in your **/etc/fstab** file on the second drive, which gives you the freedom to later also use the second drive in an external casing to boot another computer, without having Ubuntu complaining about the 'missing' (first) drive.
:razz::razz:

---

### Post by Fuel90 on 2010-05-01
> **DawieS said:**
> I recommend that:
1) you unplug the power to the first hard drive, until after the installation.
2) boot from the live CD, and install Ubuntu on the second hard drive.
3) after the installation, power down, and restore the power to your first hard drive. Adjust your BIOS to boot from the second drive (Ubuntu). 

After booting up in Ubuntu, mount all drives by clicking on them in the file browser. Open a terminal, and type the following command to update the Grub menu (include Windows 7):
```
sudo update-grub
```This procedure will ensure that nothing is changed on your first drive. Also, the first drive will not be referenced in your **/etc/fstab** file on the second drive, which gives you the freedom to later also use the second drive in an external casing to boot another computer, without having Ubuntu complaining about the 'missing' (first) drive.
:razz::razz:
Thanks!

Now I just have to find my screw driver to take my 1st HDD from my laptop.

+kudos to you sir.

---

### Post by dino99 on 2010-05-01
then install mountmanager and tweak the rights settings (system admin mountmanager)

---

