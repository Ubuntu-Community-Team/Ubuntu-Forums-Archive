---
title: "Problem with install"
date: 2010-07-05
forum: General Help
---

### Post by Goroner on 2010-07-05
Hi i recently downloaded ubuntu 10.04 , i got installed windows 7 64 bit on my pc now , i got 500gb disk , it's partitioned this way:
 
120gb where my windows is installed
50gb i made for ubuntu and it's empty
the rest about 300 and some gigs are for my dls games music etc...
 
ok so now i reboot i put ubuntu which i made to boot from usb , ok i booted ok im in ubuntu install to harddrive option , i go throught out the steps and when i come to the step where i need to pick partition i just see the hdd fully 500gb says as it's free space it doesnt see my partitions and it says up on the top of the window that there's no operating system installed on the disk , how come!? , i tried also to install first ubuntu than install windows but when i go in windows installation i see the partitions which i previously made from ubuntu installer as FAT partitions and i cant install windows on any of the free partitions which i made cause says the partitioning scheme is GPT which by windows is not supported since windows uses MBR, i mean what the hell , how am i able to install ubuntu and win 7 and run dual boot , i dont want the wgui stuff i want clean install from boot up .. please help out give me guides and tell me what should i do , here is my spec:
 
cpu: Amd phenom 2 x4 965 3.4ghz black edition
mb: asus m4a785td-v evo
vga: ati hd 4850 1gb ddr3
ram: 4gb ddr3 1333mhz
..
 
please help i want to make this work right , i know once with the ubuntu 9 version i could see my volumes and install ubuntu on the partitions i had but that was on my INTEL p4 PC and i guess it's not the amd problem or anything else related , might be the 64 bit version of my os ? hmm i dont belive it's that too =S please help!!
Thanks!!

---

### Post by Yarui on 2010-07-06
I really doubt it has anything to do with using the 64 bit versions.  I have never seen any issues with the ubuntu installer detecting a windows partition.  The way that I have always installed side-by-side is to first install Windows, making just one partition for Windows and making sure all the rest is free space, be sure not to create another partition with the intention of installing Ubuntu on it, because you would just have to remove that partition and create a new one in the correct format.  After installing Windows you should be able to choose the "install side-by-side with another OS" option.  At the top it will show a blue and orange bar to show what percentage will be Windows and what percentage will be Ubuntu.  You can just drag that to adjust it however you want.  I have always found this window to be a bit confusing if you don't know exactly what each option does, so it's understandable if you just couldn't figure out what to do here.

---

### Post by wilee-nilee on 2010-07-06
From a terminal in the live Ubuntu cd.
```
sudo fdisk -l
```
Just copy and paste this command, or just know the last character is a small case L, post the results.

---

### Post by Goroner on 2010-07-06
I tried that with sudo fdisk -l , and here is what i get i made some screen shots, btw in ubuntu in gparted says that the disk is gpt partition scheme so wierd cause it is not actualy is mbr since windows run on mbr only , but if i install ubuntu first and make partitions for windows and than go back to windows installation i cant install windows than windows says that my disk is gpt , kinda ubuntu is oposit of what windows says if my disk is gpt ubuntu sees it ok and if it's mbr ubuntu sees it as gpt  :( here are the screens including ubuntu screens gparted and windows screens of my partitions ...

here is what i get when i write the "sudo fdisk -l" command in terminal my usb was in as im booting from usb and it shows the usb too:

[IMG]http://img818.imageshack.us/img818/7555/58774119.jpg[/IMG]

and here are series of images i wrote on ever image what is going on :

[IMG]http://img138.imageshack.us/img138/8617/10410608.jpg[/IMG]

[IMG]http://img190.imageshack.us/img190/7818/27251025.jpg[/IMG]

[IMG]http://img171.imageshack.us/img171/3091/50864199.jpg[/IMG]

[IMG]http://img685.imageshack.us/img685/4924/69873266.jpg[/IMG]

[IMG]http://img822.imageshack.us/img822/109/79784545.jpg[/IMG]

sorry for big images i couldn make them smaller

---

### Post by Goroner on 2010-07-06
i think ill make it work , i did changed ahci to my bios settings and i guess that made the problems , i was trying to install mac os x for pc and i needed to set ahci so now i changed back to ide , set partition style in gparted to msdos and made 3 partitions one for windows 120gb one for files data and stuff about 280gb and the remaining about 60gb for ubuntu , since in gparted i saw my disk as msdos and formated now i think it'll work but ill report back what ive done now windows is installing and didnt reported the partitions scheme as GPT just started installing fine ,...

---

### Post by Goroner on 2010-07-06
SOLVED this thread can be closed!

---

