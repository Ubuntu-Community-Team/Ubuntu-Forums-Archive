---
title: "Grub Help"
date: 2009-10-12
forum: General Help
---

### Post by lcollier93 on 2009-10-12
I think I accidentally uninstalled the grub bootloader when I was using easybcd...soo....now I can only boot into windows 7. I have windows 7 as the main hard drive and ubuntu on the slave hard drive. how do I reinstall GRUB? I used to just boot into the main hard drive and the GRUB bootloader would come up and I could choose linux or Windows. Now it just boots into Windows 7.

---

### Post by cwbar_1 on 2009-10-12
1) Boot off the LiveCD

2) Open a Terminal and type in the following commands, noting that the first command will put you into the grub &#8220;prompt&#8221;, and the next 3 commands will be executed there. Also note that hd0,0 implies the first hard drive and the first partition on that drive, which is where you probably installed grub to during installation. If not, then adjust accordingly.

    sudo grub

    > root (hd0,0)

    > setup (hd0)

    > exit

Reboot (removing the livecd), and your boot menu should be back.

---

