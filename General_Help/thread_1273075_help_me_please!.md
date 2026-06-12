---
title: "help me please!"
date: 2009-09-23
forum: General Help
---

### Post by nagasadow13 on 2009-09-23
i was just curious about gparted and how to go about installing it. i recently installed ubuntu 9.04 as a second operating system on my asus eee pc 1000he i ran into some issues so i said 'f' it and reinstalled it. everything is fine thus far im actullay posting this thread using it but i want to get rid of the previous install and partition the current one to a larger gb of disk space. i have only 2.3 gb of disk space of which 85% is being used that leaves me with 352.7 mb of disk space remaining, which brings me to question number 2 what would be a decent amount of disk space to run a fully functional, enjoyable and useful ubuntu. i read a little about gparted and it sounds like that would be the way to go but i just dont know how to go about it correctly and safely. any advice tips or any type of help in this matter would be greatly appreciated!! thank you

---

### Post by Darkwing-Duck on 2009-09-23
Hey bro.

```
sudo apt-get install gparted
```

That should do the trick for ya!

---

### Post by blackened on 2009-09-23
Well, you can install and run gparted from within your Ubuntu install by
```
sudo apt-get install gparted
```
You can then find it in System -> Administration -> Partition Editor.

The problem with that method is that you can only alter partitions that are not mounted. So no changing the size/position of the partition that Ubuntu resides in, because Ubuntu would be running.

The way around this is to use a live CD, or in your case, a live USB. To do this, first you need to download a live CD ISO from Ubuntu.com or one of the mirrors. Then plug in a USB drive, go to System -> Administration -> USB Startup Disk Creator, select your ISO in the top box, point the bottom box to your USB drive, then hit the "Make Startup Disk" button at the bottom.

After that's finished, reboot with the USB disk plugged in, press Esc when prompted, select your USB disk as the boot device, then once the OS loads, start gparted from either the menu or terminal and edit your partitions accordingly.

---

