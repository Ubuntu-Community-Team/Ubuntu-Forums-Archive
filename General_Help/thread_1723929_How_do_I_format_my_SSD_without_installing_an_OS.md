---
title: "How do I format my SSD without installing an OS?"
date: 2011-04-07
forum: General Help
---

### Post by linuxuser12345 on 2011-04-07
Hey, still trying to fix this netbook, and I am wondering if there is a way I can format the SSD on it without installing an OS?

---

### Post by aktiwers on 2011-04-07
```
sudo apt-get install gparted
```
```
sudo gparted
```

And format through the GUI :)

Or actually I think Ubuntu has its own Disk GUI app in System => Administration => Disk Utility

---

### Post by linuxuser12345 on 2011-04-07
Um, I don't understand what to do... :/

Sorry, I am a bit new here! lol

---

### Post by aktiwers on 2011-04-08
Did you find the disk utilities?

Then pick your SSD drive and then pick Format drive :)

If you want to install gparted as mentioned, open the Terminal (applications => accessories => terminal) and type in those 2 commands mentioned above.

---

### Post by ottosykora on 2011-04-08
well netbook, then if there is no OS installed, you will need to boot from some external media first.
I suggest, you find some other computer, go to [www.partedmagic.com](www.partedmagic.com) and see there to download and produce bootable usb stick with some basic OS on it. Boot then form that stick and then you can do lot of manipulation from that GUI there. G-Parted is included there and other tools, this will then help you to format the drive.
Note: the drive to be formated, should not be mounted at the same time.

---

