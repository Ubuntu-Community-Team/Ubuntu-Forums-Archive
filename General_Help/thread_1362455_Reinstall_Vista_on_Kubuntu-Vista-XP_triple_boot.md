---
title: "Reinstall Vista on Kubuntu-Vista-XP triple boot"
date: 2009-12-23
forum: General Help
---

### Post by Liopleurodon on 2009-12-23
Hello,
at the moment I have Kubuntu 9.10, Windows Vista and Windows XP installed.  When I start my computer, the GRUB menu asks me whether I want to start up using Ubuntu or Vista.  When I select Vista, then I can choose whether to startup with Vista or XP.  I'm considering to reformat my Vista partition and reinstall Vista there.  Although I'm a bit afraid of doing so because I think Vista will overwrite my GRUB menu and will make me unable to login in Kubuntu anymore.  Can someone tell what is the safest solution to reinstall Windows Vista?

Thanks in advance!
Liopleurodon

---

### Post by zvacet on 2009-12-23
>  I think Vista will overwrite my GRUB menu

Yes it will.You will have to reinstall grub [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Leppie on 2009-12-23
> **Liopleurodon said:**
> Although I'm a bit afraid of doing so because I think Vista will overwrite my GRUB menu and will make me unable to login in Kubuntu anymore.  Can someone tell what is the safest solution to reinstall Windows Vista?

reinstall vista, grub will be overwritten but can also be easily re-installed to the mbr. just have a (k)ubuntu livecd (with the required version of grub) at hand.

---

### Post by oldfred on 2009-12-23
If you want to directly boot both windows rather than boot one window and then choose which windows see these threads:

meierfra. Repair 2 windows installs to get each to be able to have grub entries XP & Win7 or Vista
[http://ubuntuforums.org/showthread.php?t=1362297](http://ubuntuforums.org/showthread.php?t=1362297)

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

