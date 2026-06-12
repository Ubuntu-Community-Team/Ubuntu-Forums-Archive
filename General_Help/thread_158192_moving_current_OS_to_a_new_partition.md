---
title: "moving current OS to a new partition"
date: 2006-04-10
forum: General Help
---

### Post by jturnbul on 2006-04-10
been using Kubuntu for a couple of months, and have decided to make it my permanent OS.  Was using Fedora 4, and it is on my big partition on my disk.  

What I want to do is remove FC4 from hda2, and move Kubuntu(hda3) on to hda2.

Any suggestions on what would be the best method to copy it over.

---

### Post by aysiu on 2006-04-10
A live CD and PartImage.

---

### Post by jturnbul on 2006-04-10
i tried system rescue linux, and played with partimage, and qtpartimage, aswell as another program that can back drives up, or make drive images.  I wasnt to impressed, as the only option i could do was delete the drive, format, or check out the properties.  All the other options like copy, move, resize, etc were greyed out.

I was thinking of using a live CD (like kubuntu) to mount both drives then using a command like 
$ cd /mnt/hda3
$ sudo cp -arp * /mnt/hda2

Then set grub up to boot hda2, then once in hda2 use grub to install hda2 as the native grub partition.

My only concern is that thinks like symlinks might not work anymore.  Any one else attempted that way????

---

### Post by aysiu on 2006-04-10
I don't see how the options could be greyed out in [PartImage](http://www.partimage.org/Screenshots), seeing as how it's a text-based "graphical" program.

Just boot up the Kubuntu live CD, mount the two partitions and the ```
sudo apt-get update
sudo apt-get install partimage
sudo partimage
```

---

### Post by jturnbul on 2006-04-10
i used the graphical programs... anyhow talk is cheap.

I went ahead with what I suggested, and it seems to work fine.  I did get a kernel error on first boot with regards to mounting other drives, and fsck advised it couldnt fix it.  So I ammended my fstab to reflect the change in mounting of the root filesystem, and other drives, and it works perfectly now.

I have not finallized it by making the new partition the grub partition yet, as I'll give it a week or so of use, to see if any bugs pop up.

If anything bad happens I'll update this.

---

