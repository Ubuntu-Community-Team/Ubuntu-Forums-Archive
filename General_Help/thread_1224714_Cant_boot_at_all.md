---
title: "Cant boot at all"
date: 2009-07-27
forum: General Help
---

### Post by ernestolvc on 2009-07-27
Hi guys, im having a rather odd problem with my PC. I had ubuntu and XP in twi partitions wit no problem at all, but i needed hd space so i erased linux, although it seems that the file system and partition was still in my hard drive. I decided today that i wanted to use linux again so i download ubuntu and make the image cd to install, when i reset my PC and put in the live cd it didnt boot, giving the message: SOLINUX3.63 Debian 2008-07-15
                                    Unknown Keyword in configuration file
I tryed using my dreamlinux CD but again it didnt boot giving message:
                                Kernel panic - not suncing: Attempet to kill init
After thos two messages with the respective live cds nothing else happens.
I thought it was a problem with gruub, that i used to select OS at start up, so i got a disc partition manager utility, and i found that i had two partitions not recognized by windows, one 18GB that i guess was my linux partition and another 960MB partition. I thought that by formating the 18GB partition i would be able to install linux again, as i thought the problem was some linux files hadnt been totally erased and that was why live cd wasnt booting, but after erasing that partition i cant boot at all!! Grrub starts loading and gives me error 17 and freezes, thats it, i dont know what else to do as live cd wont boot either!! pls help me

---

### Post by merlinus on 2009-07-27
Faulty cd or cd drive, most likely.  Can you boot from a usb device?

---

### Post by danxx on 2009-07-27
you had dual boot so the grub was in the ubuntu partition and the indication of that position was in windows mbr, when you deleted completely ubuntu partition you deleted the file that windows was referring to in order to boot and let you chose which operative system start, you have to reinstall mbr in windows partition  if you want to boot windows, use supergrubdisk (search in the internet) the version for cd is faster or use the installation disk for windows ( I think using the command fixmbr should make the work but I am not sure ), in super grub disk chose "windows advanced" and navigate to find the option "restore mbr", if this method fails it means there is no backup of the original mbr then you have to use windows installation disk with the command ( if I remember exactly) fixboot in order to find windows installation follow by the command fixmbr, but you need to be sure of the procedure searching in microsoft documents database before attempting that system recover, there is no room for errors I only trying to explaing the problem

---

### Post by merlinus on 2009-07-27
The OP says he cannot boot from a live cd, so how do you expect your suggestions to work?

@ernestolvc

Check to make sure your cd drive is first in boot order in bios.  You will have to press an F key, or Del or Esc, to enter setup.  If you do not know which nor have system docs, you might try google to find your computer model.

---

### Post by danxx on 2009-07-27
as for the cd I suggest to use ubuntu 8.04, I bet he downloaded 9.04 one

---

### Post by danxx on 2009-07-27
the error 17 usually means the system cannot find mbr

---

### Post by oldfred on 2009-07-27
It sounds like the CD starts but then errors out. The CD needs to be verified and probably a new one made at very slow speed like 4X.

---

### Post by ernestolvc on 2009-07-28
Thanx for the ideas guys! it worked, as you suggested it was a fault when i coppied the live cd, guess i was using too much speed, i did a live cd with my sisters mac book and i got to install ubuntu just fine. Although i had the idea that by installing ubuntu and letting it create grub i would be able to boot old windows normally, guess ill have to fix it using superdrive as it freeze just after windows booting logo shows up and the pc just restarts.

But thanx very much, i got linux working :D

---

