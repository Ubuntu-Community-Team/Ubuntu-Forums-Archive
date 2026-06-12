---
title: "what is it gnu grub"
date: 2010-03-27
forum: General Help
---

### Post by pooya_mr2009 on 2010-03-27
hi every body
my grub had a problem and i reinstall it.
i had just sda7 on my grub and then i went to live and wanted to install sda2 on grub with this command:
sudo mkdir /media/sda2
sudo mount /dev/sda2 /media/sda2
sudo grub-install --root-directory=/media/sda2 /dev/sdathen i reset my computer and when grub loaded the gnu grub came
it wrote : sh:grub>
how can i solve this problem that when grub loaded i can choose my special os?
thank's a lot
bye

---

### Post by philinux on 2010-03-27
Depends if you have grub legacy or grub2. Either way reinstall grub from the livecd.

1. [Legacy way]("http://ubuntuforums.org/showthread.php?t=224351")

2. [Grub2]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html")

Ignore the windows thing about grub2. It works when grubs been borked.

---

