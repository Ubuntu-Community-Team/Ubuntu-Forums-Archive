---
title: "How do i install 11.04 on a seperate hard drive?"
date: 2011-10-01
forum: General Help
---

### Post by pkhamidar2com on 2011-10-01
Hey, ive downloaded 11.04, put it on a disk, and ive got a spare hard drive thats 40 gb but it isnt formatted or anything. 

Im wondering how do i go about doing this. I tried to install but i had no idea what to do...
Ive never dual booted before, my spare hard drive that i wish to install it on is 40gb, my current hdd is 500 gb. 

so im not too sure what i should be doing. Is there any way to install it on mainly my spare hdd? I looked at guides but i just dont get the installation bit where i have to select a drive. Thanks guys

oh and another question thats also equally as important. Does ubuntu 11.04 support 1440x900 hpw1907s monitor resolution? When i was using the live cd it wouldnt let me choose that screen resolution. 

btw pc specs if you wish to know
windows 7 64 bit
500 gb 250mBs hdd samsung spinpoint (not going to be used
40gb samsung hard drive (linux drive)
4gb of ddr3 1333mhz ram corsair xms3
ati radeon 6770 1gb GDDR5 graphics card
corsair 430w psu
msi g54 870a mobo
Generic dvd drive
AMD Phenom ii x4 955 BE
3x fans in my pc

thats it really, i dont really know if anything else is needed. So help is require here please. I really want to dual boot!

---

### Post by Basher101 on 2011-10-01
hello
it is very easy in fact...i cant show you right now as i am on windows. i will make a reboot and show you on screenshots what to do. You will have to wipe it clean and create the ubuntu partition and swap partition. Then you just have to select the **[COLOR="Red"]mount points[/COLOR]** , in other words you choose what is to be installed on what partition. I will cover this also in my screenshots so hang on a bit until i rebooted, made the screens and make circles on the buttons you have to click.

p.s. i have no idea about the monitor. Does your Live CD session look normal? no graphical issues whatsoever?

---

### Post by sanderd17 on 2011-10-01
For the first question:

You should choose for manual partition, and repartition the second hard disk (sdb). The best would be to create a 12 GB partition and mount it to root (/), a 2 GB partition for swap (use it as swap) and the rest for home (/home).

If you just do that, the bootloader (the thing that first starts and lets you choose OS) will be installed on sda (the first hard disk) and will read settings from sdb. So if you remove one of the drives, you won't be able to boot any OS.

If this is not what you want, you can choose to install the bootloader to sdb. In that case, the sda disk will be intact, but if you want to boot Ubuntu, you need to be sure that sdb is the primary disk (you can select that in the BIOS).

Some general enfo: sd stands for solid disk, and they are numbered with letters: sda, sdb, sdc ... Each hard disk has some partitions, and they are nubered with numbers. So sda can have partitions sda1, sda2, sda3 ...

Oh, and the monitor, that depends on the graphical driver you use. there might be a better one available, but I don't know.

---

### Post by Basher101 on 2011-10-01
+1 thats all you need to do. If you cant handle the information correctly i can make the screenshots for the steps. I do prefer to make the partitions with Gparted instead of inside the installer.

---

### Post by pkhamidar2com on 2011-10-01
ok thats a bit hard to understand, first bits fine but the latter bit its confusing. Okay so here is what i do right?

1) go into the installer
2) right click on the 40gb hdd and click delete
3) right click on the 40 gb hdd and then select add and then choose 12 gb partition
4) right click 12gb partition that is created and the top drop down menu choose mount, the bottom drop down choose /
5) right click the 40gb thing again and then make a 2gb partition, right click (what do i do here?)
6) The remaining hdd should be named as home....


what i find hard to understand is keeping it all seperate, like keeping windows on one hard drive, and ubuntu on the other. You say something about sdb or something, i dont understand that.... 

Should i disconnect my windows 7 hdd, and then only connect my 40gb hdd and then install?

also after install can i recconect my 500gb windows 7 one?

About that monitor, on the live CD, it was at 1280x720 which was the wrong resolution, my monitor does 16:10 not 16:9, is it possible to have the resolution at 16:10 1440x900? Because it works, but it doesnt look nice as the aspect ratio and resolution isnt optimum, its not clear, it looks blurry. 

Thanks :) Do you think its because of the live cd that the resolution is weird? i really hope i can run at 1440x900.

btw if you dont mind screen shots would be really helpful, you dont have to do it right now if you dont have time, whenever you get time as i can wait :)

---

### Post by Basher101 on 2011-10-01
From what you understood i think you do not need screenshots. When i doubt, disconnecting the internal hard drive is your BEST option as it will make the external disk /dev/sd**[COLOR="Red"]a[/COLOR]** as it is the only storage device. You also wont have to worry about the bootloader installation. As for the 2gb partition make the filesystem be SWAP (swap is dynamic memory where unused applications are moved to free up RAM.)

So all in all, in short, its best to disconnect the internal hard drive, create the partitions and mount points as mentioned above and click install. thats all you need to do for the install, the bootloader will install correctly automatically if the internal drive is disconnected.

---

### Post by pkhamidar2com on 2011-10-01
i dont know whether or not it makes a difference but im installing to an internal hard drive. 

i have 3 hard drives

500gb external (for backups of documents and files etc...)
500gb internal sata (the samsung one that i use for windows 7)
40gb internal sata (the samsung one that i will use for linux)

so should i just disconnect both my external AND internal 500gb's and just keep the 40gb inside yes? And it shouldnt conflict with any other hard drives yes?

Also a few more questions

what about that screen resolution thing?

And also i need to ask how do i change from one boot to another, do i have to keep going into the bios and changing my boot order or will it ask me at start up which os i wish to load?

---

### Post by sanderd17 on 2011-10-02
If you disconnect both internal 500GB drives, there is no risk of something going wrong, and you can just select the automated "use entire drive" option.

For your screen resolution, I can't know that. Install it and see if there are better drivers for your card.

For choosing which OS to boot.

In the BIOS you can select your hdd to boot from. If you reconnect those 500GB drives and set the windows disk to boot from in your OS, than Windows will boot. If you set the 40 GB as primary drive, than Ubuntu will boot.

If you started ubuntu and run
```

sudo update-grub

```
it will search for other OS (it also does that on installation, but since the other HDDs aren't connected it won't find any). If you than boot from the 40 GB HDD, you will be able to choose between Windows and Ubuntu.

---

### Post by pkhamidar2com on 2011-10-02
a final question i must ask, you know when you install linux, does your hard drive have to be formatted. Because that 40gb hdd is quite old, but it has windows xp on it, should i format it first or does linux installation do that for me?

if so how do i format it?

---

### Post by 3rdalbum on 2011-10-02
> **pkhamidar2com said:**
> a final question i must ask, you know when you install linux, does your hard drive have to be formatted. Because that 40gb hdd is quite old, but it has windows xp on it, should i format it first or does linux installation do that for me?

if so how do i format it?

The installer does it for you at the time.

---

### Post by oldfred on 2011-10-02
The above posts have covered most of the issues, but if you want a detailed set of instructions with screenshots:

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

I have nVidia, so I do not know ATI, but this may help:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by anur.bhargav on 2011-10-02
Hey about the Resolution.. Even my monitor is a 19-inch LCD monitor with an aspect ratio of 16:10 also known as 8:5. I see that U have a pretty good graphics card on Ur system and hence I see no issue of u not getting that resolution.

My PC just runs on 128MB on-board graphics and yet I get the 1440*900 resolution. Don't worry about the resolution just go ahead with the installation.

---

### Post by sanderd17 on 2011-10-02
> **anur.bhargav said:**
> Hey about the Resolution.. Even my monitor is a 19-inch LCD monitor with an aspect ratio of 16:10 also known as 8:5. I see that U have a pretty good graphics card on Ur system and hence I see no issue of u not getting that resolution.

My PC just runs on 128MB on-board graphics and yet I get the 1440*900 resolution. Don't worry about the resolution just go ahead with the installation.

This is a dangerous statement. It doesn't only depend on the quality of the hardware, also on the quality of the drivers. Since most producers aren't interested in Linux, the quality can be different from one graphical card to another. If there is a really good hacker that uses the same graphical card as you, you can have a better driver than Windows has. If you have a rare piece of hardware, and the producer only made a Windows driver, than your hardware will perform very bad.

The only way to find out is to try.

---

### Post by anur.bhargav on 2011-10-03
> **sanderd17 said:**
> This is a dangerous statement. It doesn't only depend on the quality of the hardware, also on the quality of the drivers. Since most producers aren't interested in Linux, the quality can be different from one graphical card to another. If there is a really good hacker that uses the same graphical card as you, you can have a better driver than Windows has. If you have a rare piece of hardware, and the producer only made a Windows driver, than your hardware will perform very bad.

The only way to find out is to try.

OK.. So there's a lot riding on the driver too.. Thank you very much for the head's up :popcorn:

---

### Post by anur.bhargav on 2011-10-03
> **sanderd17 said:**
> If you disconnect both internal 500GB drives, there is no risk of something going wrong, and you can just select the automated "use entire drive" option.

For your screen resolution, I can't know that. Install it and see if there are better drivers for your card.

For choosing which OS to boot.

In the BIOS you can select your hdd to boot from. If you reconnect those 500GB drives and set the windows disk to boot from in your OS, than Windows will boot. If you set the 40 GB as primary drive, than Ubuntu will boot.

If you started ubuntu and run
```

sudo update-grub

```
it will search for other OS (it also does that on installation, but since the other HDDs aren't connected it won't find any). If you than boot from the 40 GB HDD, you will be able to choose between Windows and Ubuntu.

And Thank you for this wonderful explanation too :p ...

---

### Post by anur.bhargav on 2011-10-03
> **oldfred said:**
> The above posts have covered most of the issues, but if you want a detailed set of instructions with screenshots:

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

I have nVidia, so I do not know ATI, but this may help:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Thank you for these wonderful links :popcorn::)

---

