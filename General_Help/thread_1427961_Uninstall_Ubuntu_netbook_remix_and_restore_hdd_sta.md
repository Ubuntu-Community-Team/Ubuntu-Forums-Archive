---
title: "Uninstall Ubuntu netbook remix and restore hdd state"
date: 2010-03-12
forum: General Help
---

### Post by dragos2 on 2010-03-12
I installed Ubuntu netbook remix on a Acer Aspire One netbook because I  forgot that Acer has a recovery hidden partition.

After I installed the Ubuntu netbook remix I found the key combination  and booted into that recovery interface and Acer recovery mode reinstalled Xp in minutes, but  after restart grub can't boot into recovered xp but it can boot into recovery mode of Acer.

Any ideas of what can I do in order to restore the system to its state  before installing Ubuntu netbook remix ? Because I don't want to loose  the license.

Any help is highly appreciated.

Thank you

---

### Post by zvacet on 2010-03-12
Maybe you can try to reinstall grub.I don't know which version do you use so I will give you links for 

[Karmic]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2")


[versions previous then Karmic]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by dragos2 on 2010-03-12
> **zvacet said:**
> Maybe you can try to reinstall grub.I don't know which version do you use so I will give you links for 

[Karmic]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")


[versions previous then Karmic]("http://ubuntuforums.org/showthread.php?t=224351")

Hmm, but what if I boot from usb Ubuntu live and delete all the linux partitions, any idea
of how to restore the original windows mbr ?

---

### Post by zvacet on 2010-03-14
Reinstall grub so you can boot in Windows.Then if you want to remove Ubuntu partitions first do [this.]("http://members.iinet.net.au/~herman546/p18.html#MbrFix.exe")After that you can delete all Ubuntu partitions.

---

