---
title: "Reseting Windows to factory preset..."
date: 2011-07-24
forum: General Help
---

### Post by medsouz on 2011-07-24
I plan on restarting windows so it will run like brand new but I installed Ubuntu through Wubi so I'm sure that it is going to delete Ubuntu off my computer when I restart so I am making a Live USB right now to add Ubuntu to my computer that way. When I reset windows will it remove the partition created by the Live USB?

---

### Post by Ezlivin on 2011-07-24
I'm not sure if you mean re-installing Windows not restarting? If you are re-installing Windows it will remove the wubi version of Ubuntu for sure. I think this is the process your looking for.

1. Re-install Windows.
2. Boot from the live USB and choose to install. 
3. Part of the installation process will ask if you to choose installation options. Choose the "install them side by side option".

After those steps reboot and you'll be shown the "grub" menu with options to boot into Ubuntu or Windows. There is some info on the Ubuntu Wiki here [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot).

---

### Post by Frogs Hair on 2011-07-24
If you want to remove Wubu / Ubuntu  , open  add /  remove programs in windows and remove  it . If you have any problems see the link . You would have no need to reinstall Windows if it is a Wubi installation unless you want to . [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

If want to start fresh , just backup your data  insert the widows disk , reformat and reinstall . Everything will be removed during the the format .

---

