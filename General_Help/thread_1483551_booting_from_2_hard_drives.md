---
title: "booting from 2 hard drives"
date: 2010-05-14
forum: General Help
---

### Post by VIPER5051 on 2010-05-14
i had vista on my first hard rive and then i got a second one for ubuntu. i have installed ubuntu on the second and was wondering if there is any way to have an option at startup on which hard drive i want to boot to

---

### Post by blueridgedog on 2010-05-14
If you install Ubuntu and let it install grub into the master boot record of the primary drive, it will give you a boot menu to select between Ubuntu and Vista.

---

### Post by bigsmitty64 on 2010-05-14
Just set your Uubuntu drive to boot first in the bios. And like blueridgedog said, you should be good to go.

---

### Post by oldfred on 2010-05-14
I like to keep drives independant. So the windows drive keeps its windows boot loader and install grub2 to the sdb drive and have BIOS boot the second drive first. gGrub2 will find windows and let you boot either. if you ever have an issue with the second drive you can still boot the first by switching order in BIOS ( or one time boot key - often f12).

When you install the important thing to look for is the advanced button on the final partition screen or when ready to install comes up. the advanced button lets you select the hard drive sda , sdb etc to install to:

Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

---

### Post by VIPER5051 on 2010-05-14
thanks everybody. i am new to ubuntu but like it so far.

---

