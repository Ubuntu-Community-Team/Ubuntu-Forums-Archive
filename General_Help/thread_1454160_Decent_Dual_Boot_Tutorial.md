---
title: "Decent Dual Boot Tutorial ???"
date: 2010-04-14
forum: General Help
---

### Post by whitetimer on 2010-04-14
Hi All

I currently have ubuntu as my main OS, which i just love, but i miss playing some windows games, so i thought i'd take the plunge into a Dual Boot.  So what i'm thinking is having Windows 7 for gaming and ubuntu lucid as main OS, so can anyone reccommend a really good tutorial on how best to do this ???

Huge Thanks 

:guitar:

---

### Post by siteregsam on 2010-04-14
I am not sure abt any tutorial for installing windows after ubuntu installation. Allocate a separate NTFS partition and then install as windows cd directs. But when u install windows after installing ubuntu u will loose grub. So ur machine will boot directly into windows without giving u an option to choose OS. 

In that case there is a tool called "Super Grub Disk(SGD)", an open source tool. So before starting ur windows installation download SGD and write it to a CD. U have to write it as a bootable  cd. So in any case of grub failure u can restore it using SGD. U can google as how to use SGD.

---

### Post by zvacet on 2010-04-14
[This]("https://help.ubuntu.com/community/WindowsDualBoot") should be what are you looking for.

---

### Post by whitetimer on 2010-04-14
> **siteregsam said:**
> I am not sure abt any tutorial for installing windows after ubuntu installation. Allocate a separate NTFS partition and then install as windows cd directs. But when u install windows after installing ubuntu u will loose grub. So ur machine will boot directly into windows without giving u an option to choose OS. 

In that case there is a tool called "Super Grub Disk(SGD)", an open source tool. So before starting ur windows installation download SGD and write it to a CD. U have to write it as a bootable  cd. So in any case of grub failure u can restore it using SGD. U can google as how to use SGD.

Thanks for the advice, what i intend to do is one Lucid is released, i will do a clean install and so start with windows 7 and then install Lucid .....

---

### Post by whitetimer on 2010-04-14
> **zvacet said:**
> [This]("https://help.ubuntu.com/community/WindowsDualBoot") should be what are you looking for.


Perfect ... Thanks

---

