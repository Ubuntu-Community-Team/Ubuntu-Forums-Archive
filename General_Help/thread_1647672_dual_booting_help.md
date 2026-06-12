---
title: "dual booting help"
date: 2010-12-17
forum: General Help
---

### Post by bradleyG on 2010-12-17
okay i am new to all of this linux stuff, I ran the live CD of ubuntu 10.10 and i really liked it. I am currently running windows xp and want to also run ubuntu just for myself to have fun and explore the OS. My only problem is that I only have one computer and its our whole family's computer. I only have one hard drive and have tried reading on how to dual boot but im a little lost. they say i have to create a new partition on my hard drive for ubuntu to use or something. So basically what i am asking is to have XP as the basic OS that i will boot into but when i want to go on i will have the option to boot into ubuntu. Is this possible? Any good guides on this, any pushes in the right direction are appreciated, thanks.

---

### Post by Saggat on 2010-12-17
Just download Wubi. It will make everything automatically.
And you can choose between OS when you turn your computer
[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

---

### Post by TeoBigusGeekus on 2010-12-17
[Here's]("https://help.ubuntu.com/community/WindowsDualBoot") a nice guide for dual booting.

---

### Post by marin123 on 2010-12-17
i suggest wubi if you want to occasionally boot ubuntu. it doesnt make any modifications to your system and if you dont like it you can remove it in Add/Remove Programs under XP.
another thing you can do is a bit more complicated, you need to defragment your xp volume and shrink the partition, unless you already have free partition on your laptop to use with linux.

---

### Post by bradleyG on 2010-12-17
thank you for all the quick replies!

i think im just going to go with wubi since it seems pretty much safe and easy, and im only going to use ubuntu occasionally.

---

### Post by bcbc on 2010-12-17
With Wubi you have to make sure you don't update packages grub-pc and grub-common. 

You can read about the issues and fixes here ubuntuforums.org/showthread.php?t=1639198

---

### Post by katykat on 2010-12-18
Probably the simplest and safest method is to get a cheap second hard drive and install it (google for HD install instructions). 

Then install Ubuntu, and you will get a choice of where to put it. 

Choose /dev/sdb

After Ubuntu installs it will come up to a menu for you to choose between ubuntu and XP. 

HOWEVER, before doing anything download and install:
[http://download.cnet.com/MbrFix/3000-2094_4-10485990.html](http://download.cnet.com/MbrFix/3000-2094_4-10485990.html)

Use it as
MbrFix /drive 0 savembr OLDWINMBR
This saves the portion of the Windows hard drive that Ubuntu will modify. 

This way if ever you want to be rid of Ubuntu or change distributions you can restore the original bootup with 
MbrFix /drive 0 restorembr OLDWINMBR
Which will put everything back to normal.

---

### Post by mastablasta on 2010-12-18
For dual booting: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Wubi uses virtualization of sort so it might be slower. also it creates one large file and if that file gets corrupted you will loose everything in your Ubuntu. there are also some other issues with wubi. but it's a great thing to try out the system. some things are also not supported in Wubi (more here: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide))

If you go dual boot (with separated partition) it is realy easy to do it with 10.04 LTS version and then you can upgrade via internet to 10.10. Check the ubuntu manual in my sig for how to install dual boot in 10.04 (page 11 onwards and with nice pics).

Basically it goes like this:
1. back up files
2. defragment the disk drive (2 times at least - 1st time will be long second run will be quite fast).
3. use windows disk manager to create separate partition (give ubuntu 20-30GB of space, in case you will want to save some data there data and programmes) but don't format it.
4. start the instalation of ubuntu (with 10.04 you just select largest unnocupied disk space for install everything else is done preety much automaticly)
5. you now have two systems on one computer completelly separate from each other. note you will be able to still access windows form Ubutnu by default. to access ubuntu part of disk from Windows you will probably need some special progarmmes. 

and that's basically it. it's a good idea to boot first from LiveCD or LiveUSb to test your hardware compatibility for any issues.

---

### Post by GrahamM on 2010-12-20
I am in a similar, but slightly different situation. 

Presently, I have two 80Gb hard drives. One has XP and the other Windows 2000. I just choose the required HD in Bios so there is no dual booting.

My choices now would seem to be:

1. Move Win2K and XP onto one drive and somehow get them both to boot. Then install Ubuntu on it's own drive.

2. Eliminate Win2K after doing some house work to retain certain capabilities and again give Ubuntu it's own drive.

3. Use wubi along with one of the windows versions which would then stay where they are. But some of warnings worry me.

4. Open a new partition on one of the windows drives and install ubuntu there. But that would create a dual booting scenario? I had that before and it was fine until I came to want to make changes in the windows O/Ss.

5. Buy a 3rd drive and install ubuntu. If I did this, presumably I could choose that drive from BIOS and have no interaction between windows and ubuntu?

6. Maybe run ubuntu off a DVD or a USB memory card? What size would be needed? I could create a partition on one of the other drives for data. Only have USB 1.1 on this machine.

Sorry - Just trying to get my thoughts straight. I have downloaded 10.1 and want to get back into Ubuntu, but it will still be a learning process for me.

---

