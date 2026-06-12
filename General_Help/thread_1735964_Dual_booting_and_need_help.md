---
title: "Dual booting and need help"
date: 2011-04-22
forum: General Help
---

### Post by xXxG0dzRagexXx on 2011-04-22
I am running on a laptop with Windows 7 pre installed on it and i want to dual boot With Ubuntu. I have everything down except that i need a DVD to burn Ubuntu on. I have A few CDs but they only hold half a gigabyte and Ubuntu is to large for them. So i decided that I will use A USB and try it. Problem is I own no USB. Then i realized that having a jailbroken iPhone i can use it as a USB seeing how i downloaded something that can make it one. I can make a Virtual USB (if thats what you call it) with a desired amount of Memory i want to use. This i have no problem with seeing how i can make a USB up to 32 gigabytes large. Now I learned i have to use this special program to make the USB boot-able and i think its called something like unetbootin. And i was wondering what this does to the USB. Will i be able to delete the ISO off my USB after i install Ubuntu on its own partition? I don't want to screw up my iPhone if i cant because once i install i plan on deleting the USB off the iPhone so i can use the rest of that space for other needs.

---

### Post by An Sanct on 2011-04-22
Welcome to the forums!

[Unetbootin]("http://unetbootin.sourceforge.net/") and other tool like that (the Ubuntu startup disk creator), set the boot sector of the USB drive to be bootable and write some of the ISO onto that disk (not the whole thing ...)

I would not advice you to use a disk, that has multiple partitions - I assume, that that is what jailbreak does to an iPhone.

I would strongly advice you to download the CD (650mb) ISO version from [here]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download") or [here]("http://www.ubuntu.com/desktop/get-ubuntu/download") (both official and located on ubuntu.com), that way, you can use the CDs you have.

---

### Post by bmathis on 2011-04-22
If you try to use your iphone as a USB flash drive, you'll end up deleting everything that it stores and just mess it up. The official ISO image that you download from ubuntu.com will fit on a standard CD with no issues. 

If for some reason you can't get it burned right, go to walmart and buy a USB flash drive for less than $20 and then use unetbootin to load Ubuntu on.

---

### Post by An Sanct on 2011-04-22
*curious* ... 
> USB flash drive for less than $20
What size would that be in the US?

PS. Consider, that xxxgodzragexxx may not be from the US...

---

### Post by xXxG0dzRagexXx on 2011-04-22
> **An Sanct said:**
> Welcome to the forums!

[Unetbootin]("http://unetbootin.sourceforge.net/") and other tool like that (the Ubuntu startup disk creator), set the boot sector of the USB drive to be bootable and write some of the ISO onto that disk (not the whole thing ...)

I would not advice you to use a disk, that has multiple partitions - I assume, that that is what jailbreak does to an iPhone.

I would strongly advice you to download the CD (650mb) ISO version from [here]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download") or [here]("http://www.ubuntu.com/desktop/get-ubuntu/download") (both official and located on ubuntu.com), that way, you can use the CDs you have.

wouldnt i need to make multiple partitions if i want to dualboot though? i might get some new CDs tommorrow becuase 650mb is to big for my CDs they only hold 512 MB each.

---

### Post by An Sanct on 2011-04-22
Using your phone as a USB drive is dodgy.

> wouldnt i need to make multiple partitions if i want to dualboot though?No, for booting, only one partition is needed, the only thing is, that it has to have a boot sector.

In short, using an iPhone as a bootable USB drive sounds dangerous (for the mobile) to me, I would avoid that as much as possible.

The smallest CD (recordable) I have ever had was my Genesis audio CD, and it was 650Mb back then (1993), please recheck the CD size, I'm sure they are 700Mb, that is enough for the distribution (mentioned in the links I gave to you).

---

### Post by xXxG0dzRagexXx on 2011-04-22
> **An Sanct said:**
> Using your phone as a USB drive is dodgy.

No, for booting, only one partition is needed, the only thing is, that it has to have a boot sector.

In short, using an iPhone as a bootable USB drive sounds dangerous (for the mobile) to me, I would avoid that as much as possible.

The smallest CD (recordable) I have ever had was my Genesis audio CD, and it was 650Mb back then (1993), please recheck the CD size, I'm sure they are 700Mb, that is enough for the distribution (mentioned in the links I gave to you).

haha yeah your right i just checked and i have a few 700MB ones but from what ive read it says that you should use partitions because you dont want Ubuntu and windows sharing Folders and such because windows can screw ubuntu up.

---

### Post by bmathis on 2011-04-22
> *curious* ... 

What size would that be in the US?

PS. Consider, that xxxgodzragexxx may not be from the US...

2GB for $8
4GB for $10
8GB for $15

not bad right?

> haha yeah your right i just checked and i have a few 700MB ones but from what ive read it says that you should use partitions because you dont want Ubuntu and windows sharing Folders and such because windows can screw ubuntu up.

When installing to a USB drive, unetbootin will wipe the drive you are using (USB or iphone) and install a bootable Ubuntu on that. When you are installing Ubuntu on your computer for good, then it will walk you through partitioning (it will recommend a dual boot and do everything for you).

Before doing this, I suggest you read up on it a bit more so you dont blow away your windows install... also do a full backup of windows, just in case. [Psychocats]("http://www.psychocats.net/ubuntu/index") has some good general info and here's a little [lifehacker]("http://lifehacker.com/#!5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony") for ya!

---

### Post by An Sanct on 2011-04-22
Yes, the *partition* I was talking about was meant as the Live USB partition (on the iPhone, you mentioned), not the install partition.

For the actual installation part, please read this [community help page]("https://help.ubuntu.com/community/WindowsDualBoot").

---

### Post by xXxG0dzRagexXx on 2011-04-22
> **An Sanct said:**
> Yes, the *partition* I was talking about was meant as the Live USB partition (on the iPhone, you mentioned), not the install partition.

For the actual installation part, please read this [community help page]("https://help.ubuntu.com/community/WindowsDualBoot").

oh ohkay sorry im very new to this. I was gonna use this tutorial here.
[http://www.youtube.com/watch?v=FmN4Pj3VWpc](http://www.youtube.com/watch?v=FmN4Pj3VWpc)
 he explains how to do partitioning while your on your windows side then burning Ubuntu on to a disk and choosing the partition's you made for ubuntu to install it on.

I want to make sure i do everything right so i dont have to do any reinstall of windows or anything.

---

### Post by An Sanct on 2011-04-22
I couldn't confirm that video, but most likely its the same as [this one]("http://www.youtube.com/watch?v=SrWqKbqDQpU&feature=related"), which I could watch.

---

### Post by xXxG0dzRagexXx on 2011-04-22
> **An Sanct said:**
> I couldn't confirm that video, but most likely its the same as [this one]("http://www.youtube.com/watch?v=SrWqKbqDQpU&feature=related"), which I could watch.

Why not? isnt it the same? should i just go through ubuntu and while on the install disk should i set up my partitions then or should i set them up while in windows?

---

### Post by vuetrip on 2011-04-22
**Simple Install Guide for dual-booting:**

Burn the ISO to a disc, restart the computer leaving the disc in the drive, boot from CD and when it gets to the bit of the installation about the partitions read the options and choose the one that says something like "Install Ubuntu alongside Windows" and all the partitioning will be done automatically for you.

**[COLOR="Red"]Warning: if you choose the option that says "Use whole/Entire Disc" you will LOSE WINDOWS[/COLOR]**

---

### Post by xXxG0dzRagexXx on 2011-04-22
> **vuetrip said:**
> **Simple Install Guide for dual-booting:**

Burn the ISO to a disc, restart the computer leaving the disc in the drive, boot from CD and when it gets to the bit of the installation about the partitions read the options and choose the one that says something like "Install Ubuntu alongside Windows" and all the partitioning will be done automatically for you.

**[COLOR="Red"]Warning: if you choose the option that says "Use whole/Entire Disc" you will LOSE WINDOWS[/COLOR]**

Can i use the windows installer to make a dual boot?

---

### Post by oldfred on 2011-04-22
No. And do not make extra partitions with windows as it will convert from basic to dynamic partitions. Windows officially says once dynamic you have to erase entire drive. There are some third party tools that work to undo it.

Make sure you have good backups.

Use Windows MMC to shrink the windows partition. Then use gparted to create partitions for Linux.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Often windows uses all 4 primary partitions:
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.
Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Real detailed instructions, not as complex as it looks as Herman gives so much info:
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by An Sanct on 2011-04-24
> **xXxG0dzRagexXx said:**
> Why not? isnt it the same? should i just go through ubuntu and while on the install disk should i set up my partitions then or should i set them up while in windows?

I couldn't confirm the video, since my internet connection was dieing on me. It is almost sure the same as the other video in the link I posted.

---

### Post by xXxG0dzRagexXx on 2011-04-24
> **An Sanct said:**
> I couldn't confirm the video, since my internet connection was dieing on me. It is almost sure the same as the other video in the link I posted.

Well the one i posted he shrinks the windows partition in windows and creates a swap space partition for ubuntu and the partition Ubuntu will be installed on. Now finally i got 25 blank discs and i have burned Ubuntu. 1 thing im worried about is getting a wireless connection. Im almost sure i will not have a connection because of the drivers. How would i obtain drivers for the connection. And another problem i have is that i dont have anything to make a back up on. Is it easy for something to go wrong because right now i just cant get a backup?

---

### Post by An Sanct on 2011-04-24
If you burned the disc, give it a try!

Boot from the CD and select "try Ubuntu, without making changes to your system", if wifi works, then it will work after install - out of the box.

And yes, in the second video, it is an install without making changes under windows. Please take a look at the other video too.

---

### Post by xXxG0dzRagexXx on 2011-04-24
> **An Sanct said:**
> If you burned the disc, give it a try!

Boot from the CD and select "try Ubuntu, without making changes to your system", if wifi works, then it will work after install - out of the box.

And yes, in the second video, it is an install without making changes under windows. Please take a look at the other video too.

Ohkay I'll try it now and give you the verdict when im done. :P

BTW I watched both vids and i think i'll make it easy for me and i will just do the partitioning in Ubuntu.

---

### Post by An Sanct on 2011-04-24
Oh no! 

I'm watching the video you suggested ... [... edited out this part , don't want to insult anyone...], the guy doesn't seem to know exactly what he is doing ... he quotes information, that was relevant  10 to 15 years ago and then proceeds to place the swap on the end of the drive... why????

Example, 4gb of ram is 4096mb and not 4000 ... so much for his "mirroring the 4gb" ...

Also the installation manages all the resizing of partitions and allocating of (enough) swap space, you don't have to care about that ...

PLEASE check the [video]("http://www.youtube.com/watch?v=SrWqKbqDQpU&feature=related") I posted! Its much simpler and explains all, that is needed to know...
Also please first try the "demo" version - try before installing.

---

### Post by An Sanct on 2011-04-24
OMG!

The guy said, that "Install along side another OS" is [WUBI]("http://wubi.sourceforge.net/") !!!!

Now I can say, what was edited out before ... this video is **total crap**, he doesn't know, what he is doing, It is a bad tutorial, please avoid it!

---

### Post by xXxG0dzRagexXx on 2011-04-24
> **An Sanct said:**
> OMG!

The guy said, that "Install along side another OS" is [WUBI]("http://wubi.sourceforge.net/") !!!!

Now I can say, what was edited out before ... this video is **total crap**, he doesn't know, what he is doing, It is a bad tutorial, please avoid it!

O.O
Which one. The one I showed you? Or the one you showed me?

---

### Post by xXxG0dzRagexXx on 2011-04-24
> **xXxG0dzRagexXx said:**
> O.O
Which one. The one I showed you? Or the one you showed me?

 oh sorry didn't realize you posted before this page. :P ohkay thanks for the tip. I'm trying ubuntu now well it's loading it, I'm on my iPhone now

So I use the vid you suggested right? :P

---

### Post by An Sanct on 2011-04-24
Yes, the one I suggested is "no bull....", no reading of what the captions say, etc.

Also, as I stated before, use "Try Ubuntu" for the first time, that way you can try it ... but if you are already at the point, where you install it, that's okay too ;)

Keep us updated :)

---

### Post by xXxG0dzRagexXx on 2011-04-24
> **An Sanct said:**
> Yes, the one I suggested is "no bull....", no reading of what the captions say, etc.

Also, as I stated before, use "Try Ubuntu" for the first time, that way you can try it ... but if you are already at the point, where you install it, that's okay too ;)

Keep us updated :)

It's still stuck on the try ubuntu part I clicked on it like 30 minutes ago and it still hasn't loaded. :/

---

### Post by An Sanct on 2011-04-24
Is the disc spinning and the light on the drive blinking?

[edit]
Well, if there is no cd-rom activity (disc doesn't spin and led doesn't blink), then you should retry.

Simply restart and when you come to the "try/install" page, wait for the cd to stop spinning and then hit "Try Ubuntu". I don't know why, but if you hit "Try Ubuntu" too fast, it goes into and endless loop. This is also present in Live USBs.

---

### Post by xXxG0dzRagexXx on 2011-04-24
> **An Sanct said:**
> Is the disc spinning and the light on the drive blinking?

Fudge. It's not. Well I think the wireless drivers work bevuase while I'm waiting I was able to log in to my wireless network.

---

### Post by An Sanct on 2011-04-24
Okay, try post [#26]("http://ubuntuforums.org/showpost.php?p=10714755&postcount=26") ... I edited it when you answered, so you probably missed it...

---

### Post by xXxG0dzRagexXx on 2011-04-24
> **An Sanct said:**
> Okay, try post [#26]("http://ubuntuforums.org/showpost.php?p=10714755&postcount=26") ... I edited it when you answered, so you probably missed it...

OH ohkay thanks. :P Let me try that now.

You are a genius. It worked. :P

Wireless. Is working. Yay!

---

### Post by An Sanct on 2011-04-24
Great! :) Happy to hear that.

---

### Post by xXxG0dzRagexXx on 2011-04-24
> **An Sanct said:**
> Great! :) Happy to hear that.

When I'm asked to allocate drive space the pnly 2 options are "Erase and use entire hard disk" and " Specify Partitions manually (advanced)" D:

Edit: I guess I have to do it manually. I have no idea what to do....
[http://cl.ly/181Y200K0l2Q0f472s0f](http://cl.ly/181Y200K0l2Q0f472s0f)

---

### Post by An Sanct on 2011-04-24
You did not get this three options? 

(screenshot from a virtual machine, with windows already installed).

---

### Post by xXxG0dzRagexXx on 2011-04-24
> **An Sanct said:**
> You did not get this three options? 

(screenshot from a virtual machine, with windows already installed).

No just 2.... I wonder why.

---

### Post by An Sanct on 2011-04-24
Wow, thats crazy...

I personally would click "Quit" in your situation, this will bring you back to the "Live Ubuntu", where you can check how your disk is partitioned currently. 

From the top menu select "System" -> "Administraton" -> "GParted Partition Editor"

If you could please make a screenshot with "Applications" -> "Accessories" -> "Take Screenshot". It should look something like the attachment I posted here.

Maybe a partition is hidden or something like that.

(PS. I tried with windows xp and win7 64bit, this picture is from win7)

addition!:
also, when in the "Test" Ubuntu, please press Alt+F2, This will bring up a "run application.." dialog, there type 'gnome-terminal', without quotes (its auto-complete, you don't have to type everything)
then copy these two commands
```

sudo parted -l 
sudo fdisk -lu

```
(note: to paste to the terminal window, use Ctrl+****+V)

And copy the result here (mark the output and press Ctrl+Shift+C, to copy to clipboard)

---

### Post by xXxG0dzRagexXx on 2011-04-24
> **An Sanct said:**
> Wow, thats crazy...

I personally would click "Quit" in your situation, this will bring you back to the "Live Ubuntu", where you can check how your disk is partitioned currently. 

From the top menu select "System" -> "Administraton" -> "GParted Partition Editor"

If you could please make a screenshot with "Applications" -> "Accessories" -> "Take Screenshot". It should look something like the attachment I posted here.

Maybe a partition is hidden or something like that.

(PS. I tried with windows xp and win7 64bit, this picture is from win7)
This is what i have....

---

### Post by xXxG0dzRagexXx on 2011-04-24
> **An Sanct said:**
> Wow, thats crazy...
also, when in the "Test" Ubuntu, please press Alt+F2, This will bring up a "run application.." dialog, there type 'gnome-terminal', without quotes (its auto-complete, you don't have to type everything)
then copy these two commands
```

sudo parted -l 
sudo fdisk -lu

```(note: to paste to the terminal window, use Ctrl+****+V)

And copy the result here (mark the output and press Ctrl+Shift+C, to copy to clipboard)

THis is my results for both. 

ubuntu@ubuntu:~$ sudo parted -l 
Model: ATA Hitachi HTS72505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  210MB  209MB   primary  ntfs         boot
 2      210MB   481GB  481GB   primary  ntfs
 3      481GB   500GB  18.7GB  primary  ntfs
 4      500GB   500GB  108MB   primary  fat32        lba


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x29e95222

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          409600   940021759   469806080    7  HPFS/NTFS
/dev/sda3       940021760   976560127    18269184    7  HPFS/NTFS
/dev/sda4       976560128   976771119      105496    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$

---

### Post by An Sanct on 2011-04-24
ok :} never mind post #34 ... Its visible from the attached image ...

You already have 4 primary partitions. You are at the limit. You can have 3  primary and 1 extended partition or 4 primary. Inside the extended you  can have as many logical partitions that you wish- the only limitation  being how much space you allocate for the extended partition.

You must remove a primary partition to install another OS.

From looking at that picture, I personally would browse the partition named "HP_TOOLS", you can do that from the top menu, "Places" -> "100 MB File System" (something like this), Also browse the windows partition ("Places" -> "280 GB File System" (something like this)), there create a folder and move the files from the 100Mb partition into there (its only 6.5mb). Then from gparted, select the "HP_TOOLS" partition, right click and select "Delete". To apply the change, click on the green check mark on top.

After that, retry the installation with the "Install Ubuntu 10.10" shortcut on your desktop. The "Install alongside" option should be available.

---

### Post by xXxG0dzRagexXx on 2011-04-24
> **An Sanct said:**
> ok :} never mind post #34 ... Its visible from the attached image ...

You already have 4 primary partitions. You are at the limit. You can have 3  primary and 1 extended partition or 4 primary. Inside the extended you  can have as many logical partitions that you wish- the only limitation  being how much space you allocate for the extended partition.

You must remove a primary partition to install another OS.

From looking at that picture, I personally would browse the partition named "HP_TOOLS", you can do that from the top menu, "Places" -> "100 MB File System" (something like this), Also browse the windows partition ("Places" -> "280 GB File System" (something like this)), there create a folder and move the files from the 100Mb partition into there (its only 6.5mb). Then from gparted, select the "HP_TOOLS" partition, right click and select "Delete". To apply the change, click on the green check mark on top.

After that, retry the installation with the "Install Ubuntu 10.10" shortcut on your desktop. The "Install alongside" option should be available.
Thank you i will tell you how this goes.

Ohkay right now im browsing HP_TOOLS and i need to create a folder place everything in it and place it in the Windows 7 Partition right?

---

### Post by An Sanct on 2011-04-24
Yes, that is the idea ... place it inside a newly created folder on the windows drive ... this way, you will have a full backup of the 'HP_TOOLS' partition.

I'm really happy to see, that you reply so fast :)

---

### Post by Quackers on 2011-04-24
Others in your position have deleted the HP TOOLS partition. It is a partition which holds diagnostic tools, as I understand it. These tools are available from HP's site.
After you delete the partition you will still need to create some unallocated space for Ubuntu to install into (100MB is not enough! :-) )
You may be able to resize the Windows C: partition to get some space. You should do this by selecting the "shrink" option from the Disk Management Window in Windows. Do not use gparted to do that - Windows may not like that.
You should also defragment Windows at least once BEFORE you shrink the C: pasrtition.
You should also reboot Windows at least twice AFTER shrinking it.

---

### Post by An Sanct on 2011-04-24
Great :)

I would *just* delete that partition too...

Isn't it so, that Ubuntu install then shrinks one of the partitions?

I'm glad, that I'm not the only one helping here!

---

### Post by Quackers on 2011-04-24
The installer can shrink the partition, yes. Sadly, it can also eat it.
Windows Vista and 7 don't like other partition tools editing its partitions.
It's safer and indeed quicker, to use Windows Disk Management screen. Defrag first/ reboot twice after, just to make sure Windows is happy.

---

### Post by xXxG0dzRagexXx on 2011-04-24
> **Quackers said:**
> Others in your position have deleted the HP TOOLS partition. It is a partition which holds diagnostic tools, as I understand it. These tools are available from HP's site.
After you delete the partition you will still need to create some unallocated space for Ubuntu to install into (100MB is not enough! :-) )
You may be able to resize the Windows C: partition to get some space. You should do this by selecting the "shrink" option from the Disk Management Window in Windows. Do not use gparted to do that - Windows may not like that.
You should also defragment Windows at least once BEFORE you shrink the C: pasrtition.
You should also reboot Windows at least twice AFTER shrinking it.

:shock: umm okay thanks for helping aswell. you guys are awesome. Im going to delete the hptools partition in ubuntu now. and shrink windows next in windows of course. I will keep you guys updated while im doing this.

---

### Post by An Sanct on 2011-04-24
Thank you *Quackers* :) you helped me and *godzrage* ...

I haven't got so much experience on complicated systems, like this one on this thread is ... I'm really happy someone jumped in :)))))))))))

Its almost midnight here ... so I'll be off to bed, I won't be here for the next day, maybe two, so please, *Quackers*, help out :)

PS. I feed ducks! ;)
*godzrage*, please post if you succeed.

---

### Post by xXxG0dzRagexXx on 2011-04-24
> **An Sanct said:**
> Thank you *Quackers* :) you helped me and *godzrage* ...

I haven't got so much experience on complicated systems, like this one on this thread is ... I'm really happy someone jumped in :)))))))))))

Its almost midnight here ... so I'll be off to bed, I won't be here for the next day, maybe two, so please, *Quackers*, help out :)

PS. I feed ducks! ;)
*godzrage*, please post if you succeed.
lol you called my system complicated. :P I've been with family and i just finished defraging my disks.

---

### Post by xXxG0dzRagexXx on 2011-04-24
> **Quackers said:**
> Others in your position have deleted the HP TOOLS partition. It is a partition which holds diagnostic tools, as I understand it. These tools are available from HP's site.
After you delete the partition you will still need to create some unallocated space for Ubuntu to install into (100MB is not enough! :-) )
You may be able to resize the Windows C: partition to get some space. You should do this by selecting the "shrink" option from the Disk Management Window in Windows. Do not use gparted to do that - Windows may not like that.
You should also defragment Windows at least once BEFORE you shrink the C: pasrtition.
You should also reboot Windows at least twice AFTER shrinking it.
When i shrink my Windows 7 partition am i also making the ubuntu partition In windows or am i doing that within the installation of ubuntu?

Also where the heck is this third partition i have? in windows i have 2. is there some sort of hidden one. i dont really plan on doing anything to it but i did also want to triple boot ubuntu, Windows 7 and OS X Snow Leopard. But i guess that cant happen since i cant add another partition from what An Sanct says.

---

### Post by Quackers on 2011-04-24
The Ubuntu partitions can be created from the resulting unallocated space after shrinking C:. These can be made with the Ubuntu installer. It's probably a moot point, but choose logical partitions rather than primary. This should create an extended partition to hold the logical partitions in. This extended partition will be your fourth primary partition. It can hold as many logical partitions as you wish to make.
You should now have 3 NTFS partitions, which should, I believe, show up in Windows Disk Management screen. One is a small (200MB) partition, which could, I suppose, be hidden - possibly. Gparted should show them all.

---

### Post by An Sanct on 2011-04-25
> **xXxG0dzRagexXx said:**
> lol you called my system complicated. :P 
Yea, well ... I don't know what goes through a manufacturers mind, when he gives you 4 out of 4 possible primary partitions on your disk, one of them 100mb big ...

Besides I know people, that gave up, even when they where given 100% accurate and secure help by forum members, because some steps seemed too complicated and/or risky to them. But I am glad, to see, you are not one of them.

Okay, now I'm really buzzing off ... 'will check this thread on my phone.

Cheers!

---

### Post by xXxG0dzRagexXx on 2011-04-25
> **An Sanct said:**
> Yea, well ... I don't know what goes through a manufacturers mind, when he gives you 4 out of 4 possible primary partitions on your disk, one of them 100mb big ...

Besides I know people, that gave up, even when they where given 100% accurate and secure help by forum members, because some steps seemed too complicated and/or risky to them. But I am glad, to see, you are not one of them.

Okay, now I'm really buzzing off ... 'will check this thread on my phone.

Cheers!
Well I ended up leaving my laptop charger over at my other families house and almost finished installation several hours ago but it died and i just got my sisters laptop charger and got it installed with no problems. This is my first time dual booting it and am now in ubuntu currently. And yeah i know what you mean. You told me it was pretty much a useless partition and i could use it to dual boot. I see no point in giving up. And there no down side to deleting it so i dont see why people would take it to be risky or complicated. and if you know how to read instructions nothing is to complicated unless there very general unspecific instructions but you guys were great help and there was not one part where i doubted you guys. One last question though. i found that 3rd partition and its the system partition. I wanted to know what that did. and if i wanted to triple boot Hackintosh, Windows 7, and Ubuntu could. i delete that or the recovery? Isnt the recovery just a clean installation of windows anyways? Or do you need that if you need to do any restore points or system recovery?

---

### Post by xXxG0dzRagexXx on 2011-04-25
> **Quackers said:**
> The Ubuntu partitions can be created from the resulting unallocated space after shrinking C:. These can be made with the Ubuntu installer. It's probably a moot point, but choose logical partitions rather than primary. This should create an extended partition to hold the logical partitions in. This extended partition will be your fourth primary partition. It can hold as many logical partitions as you wish to make.
You should now have 3 NTFS partitions, which should, I believe, show up in Windows Disk Management screen. One is a small (200MB) partition, which could, I suppose, be hidden - possibly. Gparted should show them all.
When i installed I dont think i chose logical partition. Since i wasnt able to access this while installing i just went through the installation with default settings and seeing how i just did this 4 in the morning i was just really eager to get it done and get some sleep. im guessing i couldnt do what you did inside of Gparted right? and if i did it what would be the benefits?

---

### Post by oldfred on 2011-04-25
You may want to go back and read post #15. I now understand that it was probably too much for you at that point, but now that you have installed it should make more sense. There is also a link to a post on the 4 partitions being used and what they are.

---

### Post by xXxG0dzRagexXx on 2011-04-25
> **oldfred said:**
> You may want to go back and read post #15. I now understand that it was probably too much for you at that point, but now that you have installed it should make more sense. There is also a link to a post on the 4 partitions being used and what they are.
Thanks For that. now i think i need to get this partitioning thing down well. could i still make a swap space for this thing? And im guessing i cant change whatever the default partition i made for Ubuntu's in to a extended partition?

---

### Post by Quackers on 2011-04-25
Please post a screenshot of what gparted is now showing.
Also re-running the boot script might help too.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by xXxG0dzRagexXx on 2011-04-25
> **Quackers said:**
> Please post a screenshot of what gparted is now showing.
Also re-running the boot script might help too.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Heres what i got. Looks like ubuntu automatically made swap space and it was made as a extended partition. and i got some un allocated space but im not so sure it really matters right? could i just add it to my ubuntu partiton? it irritates me looking at it. it just makes the whole thing more complicated. xD

---

### Post by Quackers on 2011-04-25
No, you can't. Settle for being irritated :-)
Now you've got 2 swap partitions. That's because you didn't use the manual partitioning option in the installer, I would think. More irritation :-)

---

### Post by oldfred on 2011-04-25
It looks like you did two full installs with the automatic creating of root (/) and swap. One is sda5 & 6 which shows not mounted (no little key symbol) and sda 7 & 8 which is mounted.

Do not worry about small MB amounts of space. That has to do with aligning partitions. It always had some space between partitions but it usually was just less than 1MB and you did not see it. Now it is a little more and you see it.

---

### Post by xXxG0dzRagexXx on 2011-04-25
> **oldfred said:**
> It looks like you did two full installs with the automatic creating of root (/) and swap. One is sda5 & 6 which shows not mounted (no little key symbol) and sda 7 & 8 which is mounted.

Do not worry about small MB amounts of space. That has to do with aligning partitions. It always had some space between partitions but it usually was just less than 1MB and you did not see it. Now it is a little more and you see it.

Yeah I guess that was the result of my laptop dying on the first installation. Sister screwed me over and said I couldn't use her charger. I'm guessing I'm just gonna have to leave the extra stuff alone right?

---

### Post by An Sanct on 2011-04-25
Not alone, you have the community behind you :)

Gretings from my vacation 
(girlfriend is sleeping and im drinking wine and browsing the internet)

---

### Post by oldfred on 2011-04-25
A bit more advanced is to convert the extra partition to /home or a /data partition.

You could delete the unused swap and expand the sda5 into that space with gparted. You will have to do that from a liveCD as no partitions in the extended can be mounted. You also will have to click on the swap partitions and right click swap off as gparted  likes to use the swap(s) to speed things up.

Three slightly different sets of instructions on moving to a separate /home. Each uses a different command to copy files.

Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  (create mount may be missing)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by xXxG0dzRagexXx on 2011-04-25
> **oldfred said:**
> A bit more advanced is to convert the extra partition to /home or a /data partition.

You could delete the unused swap and expand the sda5 into that space with gparted. You will have to do that from a liveCD as no partitions in the extended can be mounted. You also will have to click on the swap partitions and right click swap off as gparted  likes to use the swap(s) to speed things up.

Three slightly different sets of instructions on moving to a separate /home. Each uses a different command to copy files.

Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  (create mount may be missing)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
If i get rid of the extra swap, when i boot up will it still have Ubuntu boot up options? Because when i boot up this is what i get.

[http://cl.ly/2f2216280Q2R1u0p2i2L](http://cl.ly/2f2216280Q2R1u0p2i2L)

---

### Post by oldfred on 2011-04-25
I am surprised it did not find the install of Ubuntu in the other partitions. Ubuntu will show every kernel and as they get updated with new security fixes the list will grow unless you houseclean.

Why so many windows? Most have two. The vendor recovery which is just an image of you drive as purchased & your install.

If the swap is not used it will not change booting. Even if you accidentally delete the wrong swap, it still should boot but will complain & you have to manually edit fstab to fix.

---

### Post by xXxG0dzRagexXx on 2011-04-25
> **oldfred said:**
> I am surprised it did not find the install of Ubuntu in the other partitions. Ubuntu will show every kernel and as they get updated with new security fixes the list will grow unless you houseclean.

Why so many windows? Most have two. The vendor recovery which is just an image of you drive as purchased & your install.

If the swap is not used it will not change booting. Even if you accidentally delete the wrong swap, it still should boot but will complain & you have to manually edit fstab to fix.

lol dont ask me these questions i just bought the laptop not bulit it. xD lol so. Can i *House Clean* the -22 kernel out?

---

### Post by oldfred on 2011-04-25
It is usually best to keep two kernels, just in case the first has issues you can then fall back to the second.

Determine which Kernel you are using, if you delete this one, you have huge problems.
 Just run:
```
uname -a
```

In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

An easy way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by xXxG0dzRagexXx on 2011-04-25
> **oldfred said:**
> It is usually best to keep two kernels, just in case the first has issues you can then fall back to the second.

Determine which Kernel you are using, if you delete this one, you have huge problems.
 Just run:
```
uname -a
```

In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

An easy way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

ohkay i will keep them both. gonna delete the extra swap later. im not to worried about it right now. 

This is the kernel i have now.
2.6.35-28-generic

---

### Post by Quade97 on 2011-04-25
This reply was not intended, but I cannot find how to delete it, If there are any admins or admins around, please do so.

---

### Post by Quade97 on 2011-04-25
[QUOTE=In short, using an iPhone as a bootable USB drive sounds dangerous (for the mobile) to me, I would avoid that as much as possible.[/QUOTE]

About the iPhone. the only app I ever found, which is what I assume he is using, emulates a USB Mass Storage Device. The mobile user on the iPhone would be in no danger, it is only possible to emulate a Mass Storage Device because of how iTunes takes control of the partitions on the iPhone itself. This emulated USB Mass Storage Device is almost exactly like a virtual machine disk. But if necessary, formatting it from the FAT32 File System that it is may cause the application to lose track of the partition and make it un-deletable, forcing you to restore your iPhone to get rid of the lost partition. But it would still be much better to use a normal disc.

---

### Post by xXxG0dzRagexXx on 2011-05-01
> **oldfred said:**
> It is usually best to keep two kernels, just in case the first has issues you can then fall back to the second.

Determine which Kernel you are using, if you delete this one, you have huge problems.
 Just run:
```
uname -a
```

In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

An easy way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Can you go look at my new topic i made. no one seems to want to respond. :P maybe you can shine some light on things.
[http://ubuntuforums.org/showthread.php?t=1744921](http://ubuntuforums.org/showthread.php?t=1744921)

---

