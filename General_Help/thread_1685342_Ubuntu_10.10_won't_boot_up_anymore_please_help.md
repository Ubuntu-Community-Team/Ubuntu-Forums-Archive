---
title: "Ubuntu 10.10 won't boot up anymore please help"
date: 2011-02-10
forum: General Help
---

### Post by Mgllam1991 on 2011-02-10
So this is my first time posting on these forums so please bear with my noobishness. I've recently finished building my custom pc And to save money on the os I decided to go with ubuntu 10.10. I ordered the cd from the website and installed it all fine and dandy. It had been working fine until this morning when I go to turn on my pc I get this screen which says to choose an os and I'm not completely surprised by this screen since I've seen it before but when I choose any of the os I get a bunch text that I don't know how to interpret. To be more specific when I turn on my computer it takes me to this screen that says GNU GRUB version 1.98+20100804-5ubuntu3 then I get 6 options 2 of them are memtests and 4 of them ubuntu Linux genetics pad either way none of them work not even in safemode now when I click on the first option I get a bunch of #'s and some other gibberish and then At the end it says (initramfs) and it will let me type stuff after that. So yeah huge problem cause nothing will start and I can't get any work done. I still have the cd but it won't boot up from the cd. Please help. And also inwouldnt mind a command that can reformat the hardrive or some other stuff. Some specs of my computer is: AMD athlon x2 triple core 3.2 ghz, 4 gigs ram, Samsung f4 320gigs, graphics integrated with motherboard I can't remember the name but the motherboard is a biostar a880g+ and ubuntu is the only os on the system. And thanks in advance for any help or comments and excuse any misspellings but I'm typing All this on my slow iPhone 3G. 
*this is repost from desktop environment since no one over there wants to reply

---

### Post by Mgllam1991 on 2011-02-10
Please can anyone help!!!!

---

### Post by gordintoronto on 2011-02-10
Why won't it boot from the CD?

Ubuntu includes Gparted, which can be used to format a partition which is not currently in use. In other words, you boot from CD, you can format your hard drive.

---

### Post by quadproc on 2011-02-10
> **Mgllam1991 said:**
> I still have the cd but it won't boot up from the cd. Please help.
Since you can't boot from either a CD which used to work, or from a disk which used to work. it sure sounds like a hardware failure of some sort.  I would start by checking the power supply voltages; if those are OK then you probably will have to troubleshoot by substituting major assemblies such as RAM, motherboard, CPU, etc.

Once your hardware is working well enough to boot, you can use the Live CD to run gparted and that will allow you to do anything you want with partitions.

quadproc

---

### Post by glene77is on 2011-02-10
> **Mgllam1991 said:**
> Please can anyone help!!!!

Mgllam,
Why will it not boot from the Live-CD ?
The Live version runs in ram, not the HD, 
and includes Gparted for manipulating the partitions. 
Have you scratched the CD ?  :)

---

