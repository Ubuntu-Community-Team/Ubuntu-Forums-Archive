---
title: "the command to mount a drive, the graph of partitions, and the like[like disk managem"
date: 2009-07-02
forum: General Help
---

### Post by lse123 on 2009-07-02
the command to mount a drive, the graph of partitions, and the like[like disk management in XP or VISTA] are GUI or CLI in ubuntu 8.10 & 9.04 ? where this may found(menues) ?

---

### Post by prshah on 2009-07-02
> **lse123 said:**
> the command to mount a drive, the graph of partitions, and the like[like disk management in XP or VISTA] are GUI or CLI in ubuntu 8.10 & 9.04 ? where this may found(menues) ?

System-Administration-Partition Editor will give you a GUI view of partitions similar to XP's disk management MMC.

---

### Post by lse123 on 2009-07-07
I do NOT found
System &#9656; Administration  &#9656; Gnome Partition Editor.
how to appear it ?

when I click a folder in /home/ I go to usb stick ... how unmount this folder in UBUNTU 8.10 ? is needed same usb stick I used to setup this OR JUST if I delete folder (point to) USB drive, that's it and no needed any unmount procedure from Partitions Part-Menues of Ubuntu 8.10 ?

After ungrade Ubuntu 8.10 online to 9.10 I get another 18months support or NOT ?

---

### Post by prshah on 2009-07-07
> **lse123 said:**
> I do NOT found
System &#9656; Administration  &#9656; Gnome Partition Editor.
how to appear it ?

when I click a folder in /home/ I go to usb stick ... how unmount this folder in UBUNTU 8.10 ? is needed same usb stick I used to setup this OR JUST if I delete folder (point to) USB drive, that's it and no needed any unmount procedure from Partitions Part-Menues of Ubuntu 8.10 ?

After ungrade Ubuntu 8.10 online to 9.10 I get another 18months support or NOT ?

It's called Partition Editor, not Gnome Partition Editor. If it's not listed, you can install it by opening a terminal (Applications-Accessories-Terminal) and giving the command ```
sudo apt-get install gparted
```

If it still doesn't appear in the menu, pres Alt+F2 and give the below command in the box that appears```
gksudo gparted
```

To unmount your USB stick, open Places-Computer and look for your USB stick's icon (it will also be available on the Desktop, usually); then right click it, and choose "Unmount". Do _NOT_ attempt to delete the directory the USB stick is mounted at (Eg /media/disk)

9.10's updates will shut down after 11.04 is released, so you will get updates till then. Support is always available via the forums.

---

### Post by lse123 on 2009-07-08
If I upgrade online to 9.04 ubuntu then this will appear ?

---

