---
title: "Kind of a noobish question"
date: 2010-10-06
forum: General Help
---

### Post by ValtoTiger on 2010-10-06
Hello I'm still pretty new with ubuntu, but I do know a more than the basics on it. My question thugh is I am trying to extract my windows xp pro iso file but I can not it keeps giving me this error

Could not create the archive

Archive type not supported.

The reason I am doing this though (might as well explain why I am trying to extract it.) Is that my disk drive does not work so I can't install windows through CD so I figured maybe I can install windows through win (be able to run the .exe file) so I can duel boot windows or at least extract it so I can be able to extract the usb booter program (that can be launched through wine) Basically that's the main reason, so any help in trying to extract windows xp pro iso?

Please and thank you. :P (note I have winrar and 7zip installed and my iso file is located on my downloads folder)

---

### Post by Ordes on 2010-10-06
1. Wine: is a windows emulator; means it helps you to run windows software on your ubuntu; some work better than others; some dont run at all; check the wine wiki to see if it suits you or not; or just try it out by yourself.

2. if you want a dual boot system; than you have to load up the win-installer from a bootable device (rom, usb) at system startup; it will not work to load up the installer inside ubuntu; so extracting those files, and run them in wine/ ubuntu is useless

2a. A iso is a cd-image. You dont extract them, but mount them, or burn them. mount either with a software, e.g gmount-iso; or by terminal 
$ sudo mount -t iso9660 filename.iso /media/iso -o loop
where /media/iso is a folder that u first have to create by yourself in /media ; it can be any name u like (e.g $ sudo mkdir /media/anyname) 

3. In case ur rom is not working; and u want to create a win-usb installer; just google a bit; there are plenty of guides that advise you how to do it; they mostly refer to the win-cd; in your case you can just mount (not extract) the ISO, in ubuntu and than copy your files from there (onto the usb); than restart, boot from usb and install as dual boot. **however, check some guides before installing win after ubuntu as grub will be gone, and you also might face some other problems;** like windows need to be on the first partition; **also, have a working live-usb from your ubuntu, before your do any windows dual boot installing;** you will need that to fix your grub after install is done.

4. what u going to use windows for? if it is for office apps, photoshop, etc; than you might want to consider >> virtualbox << to run your windows inside ubuntu; however this is not a dual-boot; and of course your windows does not have the "power" it could have; e.g when you have a kick-a graphic card etc for gaming; this just wont work under virtualbox, than you need dual boot; to get it running, install virtualbox from software center; run; setup your virtual machine; mount your win-ISO in virtual machine; boot it up and install...

---

### Post by ValtoTiger on 2010-10-07
Alright I mounted the ISO file but now I can't find that usb booter creator to make that USB booter, do you know any that works under ubuntu? because wine crashed on wintoflash :/ 

Also I'm need windows XP becuase there are certain stuff on my laptp that only works on windows and not ubuntu (so yea graphic card and stuff)

---

