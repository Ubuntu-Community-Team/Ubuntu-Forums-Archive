---
title: "How to Format USB drive in Kubuntu"
date: 2011-05-25
forum: General Help
---

### Post by amir786_z on 2011-05-25
hi there guys.. i want to know how can i format usb drive in kubuntu ? i am using default file manager i.e Dolphin...

---

### Post by sj1410 on 2011-05-25
GParted is the best Gnome-based partition manager, its easy to use.

install it using synaptic or

```

 sudo apt-get install gparted

```

---

### Post by samigina on 2011-05-25
You dont need to install anything. Kubuntu include "KDE Partition Manager", you can find it in your menu.

---

### Post by amir786_z on 2011-05-26
> **samigina said:**
> You dont need to install anything. Kubuntu include "KDE Partition Manager", you can find it in your menu.

Thanks for replying.

But there is no option of Format in KDE partition manager. I want to know how can I format usb drive ????:(

---

### Post by amir786_z on 2011-05-27
Anybody know how do i format usb drive in kubuntu???

---

### Post by sj1410 on 2011-05-28
GParted is a Gnome-based partition manager (that can be also be used with KDE and other desktops as well).

---

### Post by amir786_z on 2011-05-29
> **sj1410 said:**
> GParted is a Gnome-based partition manager (that can be also be used with KDE and other desktops as well).

thanks for reply

the Gnome partition manager is not accepting my password and asking for pass again and again dont know wats wrong with it..

---

### Post by samigina on 2011-05-30
KDE Partition Manager does what you need, just read the help.

You need to umount the USB drive before you can format it.

Some help [here]("http://www.kde.org/applications/system/kdepartitionmanager/")

---

### Post by 243kof on 2011-06-14
Hi there amir786_z. I had the same question as you, and I think I have found the solution using KDE Partition Manager: What I did was right click on the partition of my usb stick (/dev/sdb1 in my case), select properties and check the box "Recreate existing filesystem". This erased everything in my usb stick. Just to be sure, I created a folder with a file in it afterwards to verify I haven't damaged the device :)
Hope this helps.

---

### Post by Natanael on 2011-11-19
I have a problem with it. I want only to change the name of my SD card. But KDE Partition Manager doesnt show it. I can get on it with other programs, copy my files, but KDE PM doesn't see it. Any ideas?
The strange thing, that it sees other Pendrives.

---

