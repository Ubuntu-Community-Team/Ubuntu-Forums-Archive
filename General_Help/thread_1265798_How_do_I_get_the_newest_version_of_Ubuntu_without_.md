---
title: "How do I get the newest version of Ubuntu without a CD?"
date: 2009-09-13
forum: General Help
---

### Post by faim2600 on 2009-09-13
I don't have a CD burner and I just wanted to upgrade.  I have version 8.04.  Thanks!

---

### Post by zephyrcat on 2009-09-13
Go to System > Administration > Software Sources. Enter your password. Click on the Update tab, then look at the Release Upgrade dropdown. Change the setting to "Normal releases". Then go to System > Administration > Update Manger. You will be offered the option to upgrade to 8.10. You will have to upgrade to 8.10 before you can upgrade to 9.04.

---

### Post by katakaio on 2009-09-13
You can also use the command line with **sudo do-release-upgrade** if you prefer that method. Hope you enjoy the upgrade!

---

### Post by Ms_Angel_D on 2009-09-13
Not sure if you mean you only have a cdrom or just no cd-drive at all. But if you do have a cd-rom & just no burner and if  your patient you can order the free cd from shipit or you can wait until october for the new version to come out and order the cd then.

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by fluffman86 on 2009-09-13
I always use a USB stick.  

First:
```
sudo apt-get install usb-creator
```
Then download the ISO you want to use from [http://www.ubuntu.com](http://www.ubuntu.com)
Go to System > Administration > USB Creator and just point it to the iso you downloaded.  You'll be up and running in minutes. :)

---

