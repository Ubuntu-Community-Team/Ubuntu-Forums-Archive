---
title: "Few questions"
date: 2009-11-19
forum: General Help
---

### Post by Corey4666 on 2009-11-19
okay so I plan to dual boot with windows vista, and ubuntu 7.10. 

A thing to keep in mind I am a dial up user. I also plan to use Vista for gaming mostly. Also I am using a big desktop PC not laptop.


My questions are:

Some software is big over 60mb's is there a good reliable/safe source where I can download programs? I plan to download them at friends house and put on a usb flash drive. (.deb) packages.


Pretty much same as above^ but Ubuntu has a lot of updates, what are some ways I can get them installed on my PC with such a extremely slow connection? (4-5 kb/s sec) Almost like the question above, is there a manual way to update with .deb packages? Also would it hurt to skip updates? I don't update windows vista at all, except for 1 time. 



Okay now for installing question (biggest one I need help with)

I got ubuntu 6.x - 7.10 (plan to use 7.10) From pretty much when I first ever used Ubuntu linux. I planed to re size my main partition which is 250 gigs. I only have 111GB left, I would re-size it to like.. 85 gigs. Then I know about /home and /swap partitions. I need advice on how to set up my 80 gigs so my system is easily upgradable once I get a copy of ubuntu 9.10 ver. And when I mean easily upgradable, I want my /home and my system settings, programs, system updates to still be intact with my new install of ubuntu 9.10v. That way I don't need to get all my programs back and settings. ( I don't know where system settings etc etc is all stored )



Also I recently got a 82.3GB SATA HDD. *my 250 gig hdd I got now is a IDE*  Anyways I was thinking if I could get the SATA all plugged in and setup I could use this for my whole Ubuntu OS. I have had a old PC in the past where I have installed WindowsXP on the master HDD. Then Ubuntu on the slave HDD, The GRUB loader failed to add my Ubuntu OS to the bootlist. Which is where Linux gets very complicated for me.



Now I have to do all this cautiously because I got a lot of programs and files that I really would hate to lose if I messed up on my install. I backed up as much as I could but... There is only so much backup space I got.  


I am mostly interested in how to partition my system so that all my settings are there, and programs etc. when i upgrade to 9.10v ;)

---

### Post by undecim on 2009-11-20
My thoughts:

For installs/upgrades, look at [http://keryxproject.org/](http://keryxproject.org/). I've never used it before, but I hear good things about it. (checking it out is on my TODO list, but I haven't gotten around to it, yet)

I would recommend that you do a clean install of 9.10. If you can backup your home directory, that will save all your user settings, and you can use Keryx and a friend to reinstall any programs you need.

Also, it won't do you much good to save your programs, because to install the 9.10 version of each program, the new package will need to be downloaded.

I'd say that installing Ubuntu 9.10 on the second drive would be your best option. That way, you can copy your old /home directory over after you have installed and know that everything works. Just make sure you pay attention during the partitioning step of the installation, so that you don't install it on the wrong drive.

---

