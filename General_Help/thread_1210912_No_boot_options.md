---
title: "No boot options"
date: 2009-07-12
forum: General Help
---

### Post by STCC on 2009-07-12
I just installed ubuntu-9.04-desktop-amd64 and it seemed like the installation went fine... I chose the option to dual boot with windows XP but after the installation completed and the computer rebooted it just went straight into XP with no option to boot into Ubuntu... I deleted the ex3 and swap partitions in windows and tried to install it again and got the same thing. 
Does anyone know what's wrong?

---

### Post by yeaitsdark on 2009-07-12
What method are you using to install? Live CD i guess? Also, it's only a single hard drive in your machine yea? Just checking.

---

### Post by STCC on 2009-07-12
Yeah, live cd. I have 2 HDDs in there but i only selected the one with XP on it when installing. 
In windows disk management there are two partitions it can't recognise, one 2.33Gb and another 173Mb. They should be the ex3 and swap partitions.

---

### Post by yeaitsdark on 2009-07-12
In that case my thinking is the "boot" order of your drives really. Is the XP drive 2nd on the list when you've installed? It may just be putting grub in the MBR of the secondary drive and properly installing the files to it While leaving untouched the XP loader in the MBR of that first drive. Pretty much just a guess based on that.

---

### Post by STCC on 2009-07-12
I think you're right, the second hard drive was first in the boot options. I reinstalled GRUB and it's all good. 
Thanks for the help.

---

