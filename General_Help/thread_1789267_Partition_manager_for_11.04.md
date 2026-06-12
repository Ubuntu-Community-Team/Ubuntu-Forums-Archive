---
title: "Partition manager for 11.04"
date: 2011-06-23
forum: General Help
---

### Post by matrixebiz on 2011-06-23
Hello, is gparted still the recommended Partition Manager for resizing my Ubuntu 11.04 partition? I have my laptop booting Windows 7 and Ubuntu and didn't give it enough space when I initially installed Ubuntu, I didn't think I would like it so much and start using it more as I've installed a few of my needed Windows programs successfully :) (MT4, etc...)

Thanks

---

### Post by yetiman64 on 2011-06-23
Gparted works very well on all the Linux filesystems (11.04 uses ext4 by default) so basically yes it is. The recommendation for resizing/moving Windows partitions, if you need to do that, is to use Windows tools since Vista and on, also to defrag them thoroughly (2 or 3 times) first.

For resizing your 11.04 install you may want to consider downloading and burning a gparted live cd image as you cannot alter a partition while it is in use (that is from gparted installed in your Ubuntu install). gparted live cd is available from [[COLOR=Blue]--here--[/COLOR]]("http://gparted.sourceforge.net/download.php"). I would recommend the "stable" release iso for download. The checksums for the downloads are on the same page.

Edit: clean forgot gparted is on the Ubuntu live cd till I saw 3miro's post OP :-) that is just as good if you already have the Ubuntu live cd.

---

### Post by 3Miro on 2011-06-23
The best way to resize partitions is when they are not being used. Windows can resize a partition in use, but there are some big limitation to it.

You need to boot from either a live CD or live USB:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Select "Try Ubuntu" so that you don't change anything on your system. Then you can use Gparted (search for it in from the menu, in the classic menu it is under System -> Admin). Gparted will let you resize the partitions.

---

### Post by matrixebiz on 2011-06-23
Ok, thanks for the info so should I resize (shrink) my Windows 7 partition _first_ using a windows utility then when I use the Ubuntu Live, expand to the extra space thats on the drive?
Or just use the Live CD and it will shrink my Windows 7 at the same time increasing my Ubuntu partion?

---

### Post by 3Miro on 2011-06-23
It is recommended to use the windows utility for the windows partition. However, I have used gparted to resize a windows partition and it worked fine.

Either way, you should backup all important data just in case something goes wrong.

---

### Post by matrixebiz on 2011-06-23
> **3Miro said:**
> The best way to resize partitions is when they are not being used. Windows can resize a partition in use, but there are some big limitation to it.

You need to boot from either a live CD or live USB:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Select "Try Ubuntu" so that you don't change anything on your system. Then you can use Gparted (search for it in from the menu, in the classic menu it is under System -> Admin). Gparted will let you resize the partitions.

How do I switch back and forth to the Classic menu? With the Left side menu Applications button, I don't like having to keep selecting Show all 86 items then search for what I want to run. Thanks

EDIT: not at home yet but read it's in the Login Screen settings

---

### Post by yetiman64 on 2011-06-23
Just had to boot a Natty live cd to check that ;), and am posting from the live cd. The live cd defaults to the classic interface, so you can just go to System > Administration > Gparted Partition Editor, and click on it. Cheers, yetiman64

---

