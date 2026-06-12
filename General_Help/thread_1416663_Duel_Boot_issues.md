---
title: "Duel Boot issues"
date: 2010-02-26
forum: General Help
---

### Post by Clark76 on 2010-02-26
I had bought a system which originally had Vista on it and so I installed Ubuntu as a duel boot and everything worked fine (except Vista which is a hunk of junk;))

I decided to upgrade Vista to Windows 7 and now when I boot up I am not longer getting the option to boot into Ubuntu.  I had expected for grub to not come up and mistakenly thought Windows boot loader would still allow me to boot into Ubuntu.  Through Windows I have confirmed all my Ubuntu partitions are there.  I am running 9.10 currently.

Any help getting the Grub boot loader working again would be greatly appreciated .

---

### Post by TitanusEramius on 2010-02-26
Well, it's sounds to me like Windows 7 have overwritten GRUB.

I can recommend this reading:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Clark76 on 2010-02-26
Thanks for the link :)

---

### Post by drs305 on 2010-02-26
This will most likely restore Grub:
[How to restore the Ubuntu/XP/Vista/7 bootloader ]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by Clark76 on 2010-03-01
Thanks for the help.  I was able to restore Grub2 back on my system.  Then all I had to do was run: sudo update-grub2 to rebuild Grub since I had made some adjustments to the windows partitions.

Thanks once again:)

---

