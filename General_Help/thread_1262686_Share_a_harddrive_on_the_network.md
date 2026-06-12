---
title: "Share a harddrive on the network"
date: 2009-09-10
forum: General Help
---

### Post by lachlan438 on 2009-09-10
Hey I am new to Linux and have found ubnutu I am using the netbook remix on my mini note and at first there was no sound but that was fixed by installing different drivers. so I am quite happy with ubuntu but what I need to know how to do this.

Right now I have a really old windows computer that has two harddrive's one of them is used for the operating system and all its files and the other is full of music videos ROMS and what have you entertainment. This computer shares that drive over my lan in the house it can be accessed though a network drive in on my windows vista computer and though wifi on my mininote. 

what I want to do is change my old XP install to ubuntu only thing stoping me is how do I set everything up so that ubutnu is sharing the drive to the whole wide world really I mean it I dont want to put on any kind of security I just need root access to the second drive in this computer from my windows vista computer and my mininote. I also want to be able to run open office org and have the GUI that plane ubuntu has. 

SO how do I make a network drive step by step please I dont have it installed atm only because I dont know how to set it up I can do the windows vista part just not the ubuntu part

thanks.

---

### Post by VipX1 on 2009-09-10
You don't need a network drive as long as the Music/media drive an the XP machine is FAT32....
Just install Ubuntu on the XP machine on the master hard drive along side XP. As I'm sure you know the install on the Live CD gives that option. Then when Ubuntu is on the old XP machine you'll have the GUI and your Music/Media hard drive will be available to you on the Desktop as an icon. Right Click on that icon and Share it and allow Guests. Then you can access it on the LAN. The Music drive has to be FAT32 or Ubuntu will not see it. If it is an old XP install it might be FAT32 but most XP installs are NTFS these days.
If you do it that way at least you have the option of going back to the XP install if some part of the Ubuntu OS isn't compatible. While you find a solution you can but the XP back on. It's always good to have a back up plan.
If on the other hand you mean "how to find a network drive" and you have already got the Music/media drive networked as a LAN device in such away that your Vista machine can see it then Ubuntu will see the drive too in the Ubuntu Browser under 'Network' 'Windows Workgroup'.

---

