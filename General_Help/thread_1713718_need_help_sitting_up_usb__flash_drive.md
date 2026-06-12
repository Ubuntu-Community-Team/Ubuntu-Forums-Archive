---
title: "need help sitting up usb  flash drive"
date: 2011-03-24
forum: General Help
---

### Post by newbiegary on 2011-03-24
what is it with you high tech people. every site i go to. i get the run  around.is my English not good enough. if you prefer i can say it in  Russian.my question is an easy one. on my vista. i have Linux operating  system.  i use Ubuntu.i have a usb flash drive. all i want to no is how  to setup usb flash drive to work on Ubuntu. i don't want to use usb to  put Ubuntu on my vista. its already on here.i,m going to use usb flash  drive to put a smaller operating system on another computer. a windows  xp.i don't think i can put it any simpler then that. so please stop  giving me the run around. if you can answer the question. thats fine. if  not then move on.

---

### Post by seawolf167 on 2011-03-24
Ubuntu can read most file types (NTFS, ext2/3/4, FAT, etc.), so the limitation would be Vista reading the USB Flash drive. In order to make Vista happy, you'll have to format the drive as NTFS or FAT.

You can format it by right-clicking "My Computer", selecting "Manage", then under "Disk Management" right click your USB drive and select "Format". You can also format it through GParted from Ubuntu (System -> Administration -> GParted). 

If you are going to format it in Ubuntu as NTFS, you'll also want to get before you use GParted

```
sudo apt-get install ntfsprogs
```

Then you can put whatever you'd like on the flash drive from either OS and take it to any other computer and use it.

If you'd like to create a bootable flash drive for any reason, [UNetbootin ]("http://unetbootin.sourceforge.net/")is the easiest way to get that working.

---

