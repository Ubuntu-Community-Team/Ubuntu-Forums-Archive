---
title: "duel boot fedora and ubuntu"
date: 2010-08-24
forum: General Help
---

### Post by shaolin788 on 2010-08-24
i have fedora 13 installed on my computer i have set it up to take only half of the hard drive i would like to install ubuntu to take up the other half iv tried duel booting in the past but every time iv tried there was no boot menu is there anything special i should do?

---

### Post by utnubuuser on 2010-08-24
If Fedora is installed first, Ubuntu should pick up the installation and include it in the boot menu.

Last time I installed Fedora after Ubuntu, Fedora's installer didn't include Ubuntu in the grub menu, but installing Fedora first and Ubuntu second worked out ok...

---

### Post by sikander3786 on 2010-08-24
> **shaolin788 said:**
> i have fedora 13 installed on my computer i have set it up to take only half of the hard drive i would like to install ubuntu to take up the other half iv tried duel booting in the past but every time iv tried there was no boot menu is there anything special i should do?

Nothing special really.

I installed Windows 7, then Fedora which picked up Windows in the Boot Loader and finally Ubuntu which picked both of them.

Just install Ubuntu, let the boot loader install in the default location and you will be Dual Booting.

Regards.

---

### Post by garvinrick4 on 2010-08-24
> **shaolin788 said:**
> i have fedora 13 installed on my computer i have set it up to take only half of the hard drive i would like to install ubuntu to take up the other half iv tried duel booting in the past but every time iv tried there was no boot menu is there anything special i should do?
In the install pages of Ubuntu when you get to page 8 there will be an advanced tab
in lower right of page just make sure you click on it and put grub in sda and it will give
you grub2 which Ubuntu now uses and Fedora 13 still uses grub legacy and will be over written by Ubuntu. When it boots into Ubuntu give it this code:

```
sudo update-grub
``````
sudo grub-mkconfig
```Just so you are sure to get both Operating Systems in grub menu and get a fresh config file.

---

### Post by shaolin788 on 2010-08-24
ok i figured it out and thank you very much for the help i just need to manual set how much space it would take up on my hd

---

### Post by garvinrick4 on 2010-08-25
Some links to partitioning with gparted.





[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted) 
 
 [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html) 
 

 [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) 
 [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) 
 

 [http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/) 
 

 [https://help.ubuntu.com/community/Ho...sAndPartitions](https://help.ubuntu.com/community/Ho...sAndPartitions) 
 [https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

