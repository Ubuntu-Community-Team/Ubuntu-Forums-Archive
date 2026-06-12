---
title: "Bootable CD"
date: 2011-02-27
forum: General Help
---

### Post by wiggly81 on 2011-02-27
ok so i want to create a bootable CD containing some usefull progs.. ie gparted live / clonezilla live / Memtest etc.... how would i go about making this cd with a choice window to select what application i want to run ?

---

### Post by Megaptera on 2011-02-27
You could use Remastersys. For instance install Ubuntu, remove apps you don't want, install those that you do want and then create CD/DVD with Remastersys.
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by yusof125 on 2011-02-27
i must to try this. thanx for guide.

---

### Post by Megaptera on 2011-02-27
> **yusof125 said:**
> i must to try this. thanx for guide.
You're welcome! It's how I make a backup disc so that if I mess up I can re-install quickly, it works for me.

---

### Post by wiggly81 on 2011-02-27
What I'm actually wanting to do is this
I have a live cd for memtest a live cd for gparted and a live cd for clonezilla 
Now they could all fit on 1 cd and that's what I want to do so I don't have to hunt for cds all day lol

---

### Post by wilee-nilee on 2011-02-27
There are several multiboot usb setups as well that is what I use, here is a windows and linux loadable link.
[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)

Here is what's on a 16 gig I have, the maverick and the knoppix are persistent. This loader normally only allows one persistent but I think the knoppix had a built in one.
Clonezilla
Parted Magic (Partition Tools)
Gparted (Partition Tools)
Ubuntu 10.10 
BitDefender Rescue CD (Virus Scanner)
Kaspersky Rescue CD (Virus Scanner)
Partition Wizard 5 (Partition Tools)
Slax 6.1.2 Graphics mode (KDE)
Install Windows Vista/7
SliTaz 3.0
Puppy 5.2
Supergrub2
Knoppix

---

### Post by Megaptera on 2011-02-27
A quote from link below "If you ever wondered how you could combine multiple ISO files and how to burn a single ISO image file onto DVD that could let you use all of them, the answer lies in this article."

[http://www.makeuseof.com/tag/combine-multiple-iso-images-burn-single-bootable-iso-image-file/](http://www.makeuseof.com/tag/combine-multiple-iso-images-burn-single-bootable-iso-image-file/)

Further quote "You can have GParted for partitioning, Backtrack for Pen Testing, System Rescue CD as a rescue CD, CloneZilla to clone your hard disk, DBN to completely wipe off data of your hard drive and then there are hundreds of Linux distributions that you can find as a bootable CDs. Make a pick and you add another one to the stack of CDs.
While all these tools are fine and dandy, carrying a number of CD&#8217;s along is too much of a hassle. Add to that the fact that many of the above are considerably smaller than a CD&#8217;s 700MB capacity."

Hope this helps?

---

### Post by wiggly81 on 2011-02-27
perfect!

thank you so much :D and so simple i feel dumb now lol

---

