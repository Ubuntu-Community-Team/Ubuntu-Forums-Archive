---
title: "ubuntu reboots after grub"
date: 2010-05-11
forum: General Help
---

### Post by pankajmore on 2010-05-11
Hello everyone, 
I have ubuntu 9.10 and windows xp installed as dual-boot on my lenovo pc since a few months.Ubuntu was working great until few days ago,there was a power outage when the system was running ubuntu and it rebooted(hard).Since then I m unable to use ubuntu.Grub and windows xp is working all right but when i choose ubuntu , all i get is a busy mouse for a few seconds and just before the rest of the gui comes up , it crashes and automatically reboots.In recovery mode, i m able to login but startx behaves similarly.What is more interesting is that all my live cds and live usbs such as ubuntu 8.04,lucid,xubuntu,lubuntu,chakra(arch linux),mint all behave similarly i.e just before the gui they crash and reboot.So is it a hardware fault or something else related to xserver,xorg? I am finding it very hard to live without linux.Please give some suggestions as to how to detect the cause of the problem, any help is greatly appreciated.

---

### Post by dcstar on 2010-05-11
> **pankajmore said:**
> Hello everyone, 
I have ubuntu 9.10 and windows xp installed as dual-boot on my lenovo pc since a few months.Ubuntu was working great until few days ago,there was a power outage when the system was running ubuntu and it rebooted(hard).Since then I m unable to use ubuntu.Grub and windows xp is working all right but when i choose ubuntu , all i get is a busy mouse for a few seconds and just before the rest of the gui comes up , it crashes and automatically reboots.In recovery mode, i m able to login but startx behaves similarly.What is more interesting is that all my live cds and live usbs such as ubuntu 8.04,lucid,xubuntu,lubuntu,chakra(arch linux),mint all behave similarly i.e just before the gui they crash and reboot.So is it a hardware fault or something else related to xserver,xorg? I am finding it very hard to live without linux.Please give some suggestions as to how to detect the cause of the problem, any help is greatly appreciated.

Do a fsck on the partiton in recovery mode.

---

