---
title: "winows 7/ubuntu"
date: 2010-03-24
forum: General Help
---

### Post by don wan on 2010-03-24
I have upgraded from windows X P-3 TO WINDOWS -7, I reinstalled ubuntu 8.4 as an application as I did on X P , But the duel boot menu dose not show up. On X P a boot menu gave me a choice of what operating system to use, but this time it dose not show up,
Is 8.4 compatible with windows-7??? Thank for any help you can give me.
don wan

---

### Post by fatfranko on 2010-03-24
I personally haven't tried, but this might help:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Tell me if that helped.

---

### Post by wilee-nilee on 2010-03-24
> **don wan said:**
> I have upgraded from windows X P-3 TO WINDOWS -7, I reinstalled ubuntu 8.4 as an application as I did on X P , But the duel boot menu dose not show up. On X P a boot menu gave me a choice of what operating system to use, but this time it dose not show up,
Is 8.4 compatible with windows-7??? Thank for any help you can give me.
don wan

Does as a application mean a wubi install?

8.04 is compatible with W7.

A little more information is needed what is on the computer now and in what order was it installed.

---

### Post by don wan on 2010-03-24
windows 7 is on computer now,I removed ubuntu just in case it wasn't compatible, WIN-7 WAS THE FIRST INSTALL

---

### Post by Serpher on 2010-03-24
If you shrink that partition now by right clicking my computer, going to Manage, then disc management and right clicking on your partition and clicking shrink. Shrinking it down at least 20G, preferably more (This is how much Ubuntu will run on), then install Ubuntu, you will get the Windows entry in the GRUB menu automatically.

In the future to fix this in any version 9.04 and below, boot from a live cd and execute the following commands:

```
$sudo grub
> setup(hd0,0)
> root(hd0,0)
> quit
```

The first 0 is your harddrive, starting at 0, and the other number is your partition number for Ubuntu. To check that go into System --> Administration --> Disk Utility, and see click on your Linux partition. It should say something like /dev/sda2. Just subtract 1 off the sda number and that's the number for the second 0. After than, reboot, take the CD out, and GRUB will boot with Windows there.

---

### Post by don wan on 2010-03-24
FATFRANKO,
I did not try to do the partition thing,as I am fairly new at this . Thanks for your help

---

### Post by Mark Phelps on 2010-03-25
Don wan:  The problem is most likely the combination of Wubi install and Win7.  It's not particularly related to the version of Ubuntu that you install.  

There are ongoing problems with using Wubi with Win7 -- it's not in the supported list of OSs for Wubi, and lots of folks have NOT been able to make it work.

---

