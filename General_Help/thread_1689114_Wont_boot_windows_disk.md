---
title: "Wont boot windows disk????"
date: 2011-02-16
forum: General Help
---

### Post by ledwardz on 2011-02-16
Hey, i need to go back to windows then dual boot with ubuntu 10.10 i have tried the following. Im really starting to lose my rag with this.

1. wont boot xp, vista or win 7
2. will boot ubuntu cd so isnt a problem with the disk drive
3. 2 partitions - 1 ntfs and 1 that ubuntu is on.
4.tried running vista in wine but says no space despite partition being ntfs
5.Boot from cd- hold in F11 doesnt work says boot from cd then goes to ubuntu
6.Not to sure if keyboard fucks up at this point cos it says press any key and i do but it does nothing also when selecting which partition to load it wont go down, the arrow keys don't work but it will load boot menu etc so dunno wotts going on there.
7. tried going into advanced bios and setting cd rom as primary boot option- doesn't work
8. Tried reformatting whole hardrive with ubuntu disk but got no where cos it still meant u had to install ubuntu after reformat.

any other options?

is there any way to just completely wipe the hard drive and do a clean reinstall of windows?

Thanks for any help, Lee.

---

### Post by Megaptera on 2011-02-16
You could boot in to live CD and use GParted to format whole drive as NTFS, install Windows. Then use Gparted to creat seperate partition on which to install Ubuntu.

I did that and have approx 20gb Vista, 10gb Ubuntu and 120gb NTFS for 'storage' which both can access.
It may not be the most elegant way but it worked for me!!

---

### Post by 3Miro on 2011-02-16
> **ledwardz said:**
> Hey, i need to go back to windows then dual boot with ubuntu 10.10 i have tried the following. Im really starting to lose my rag with this.

1. wont boot xp, vista or win 7
2. will boot ubuntu cd so isnt a problem with the disk drive
3. 2 partitions - 1 ntfs and 1 that ubuntu is on.
4.tried running vista in wine but says no space despite partition being ntfs
5.Boot from cd- hold in F11 doesnt work says boot from cd then goes to ubuntu
6.Not to sure if keyboard fucks up at this point cos it says press any key and i do but it does nothing also when selecting which partition to load it wont go down, the arrow keys don't work but it will load boot menu etc so dunno wotts going on there.
7. tried going into advanced bios and setting cd rom as primary boot option- doesn't work
8. Tried reformatting whole hardrive with ubuntu disk but got no where cos it still meant u had to install ubuntu after reformat.

any other options?

is there any way to just completely wipe the hard drive and do a clean reinstall of windows?

Thanks for any help, Lee.

I don't understand what the problem is and what is it that you are trying to do exactly. In a dual boot setup WinXP and Ubuntu you need at least 2 partitions (third is recommended for Linux swap). In a dual-boot with Win7 and Ubuntu you need at least 3 (Win7 uses two partitions). If you have a correctly set dual-boot system you do not need a liveCD, you should be able to just boot and then given a menu to select Ubuntu or Windows.

1. How many windows versions do you have installed and what do you mean they will not boot.
2. the disk drive is fine, but the CD itself may be damaged. If you are trying to boot a Windows CD, then the CD may be damaged.
3. Read above on how many partitions are needed.
4. You can only run individual Windows programs in wine. You can never run an entire copy of windows. If you want to run an entire copy of windows, then use Virtual Box.
5. What CD do you have inserted, is it an Ubuntu liveCD or windows install CD or windows Upgrade CD. Are you sure the CD is bootable.
6. What keyboard are you using. There have been some issues reported with wireless keyboards and the boot menu. Tell us the model of your keyboard.
7. You can reformat the HDD with the Ubuntu LiveCD. Select "Try Ubuntu" and then go to System -> Admin -> Gparted. Note that reformatting will destroy all data on the HDD so BACKUP EVERYTHING IMPORTANT. However, once you reformat your HDD, any OS on it will be gone. You will have to install either Ubuntu or Windows.

Doing a clean reinstall of windows requires a Windows install CD. Then boot form the CD and go from there.

---

### Post by ledwardz on 2011-02-16
> **Megaptera said:**
> You could boot in to live CD and use GParted to format whole drive as NTFS, install Windows. Then use Gparted to creat seperate partition on which to install Ubuntu.

I did that and have approx 20gb Vista, 10gb Ubuntu and 120gb NTFS for 'storage' which both can access.
It may not be the most elegant way but it worked for me!!


so when i put in the ubuntu 10.10 disk, what do i click on to format the whole hard drive? The partition bit? if i click on that then click forward i still have to install ubuntu do i not? Thanks for the reply also.

---

### Post by 3Miro on 2011-02-16
> **ledwardz said:**
> so when i put in the ubuntu 10.10 disk, what do i click on to format the whole hard drive? The partition bit? if i click on that then click forward i still have to install ubuntu do i not? Thanks for the reply also.

Go to System -> Admin -> Gparted and you can reformat without the need to install anything. BACKUP EVERYTHING IMPORTANT FIRST.

---

### Post by ledwardz on 2011-02-16
> **3Miro said:**
> I don't understand what the problem is and what is it that you are trying to do exactly. In a dual boot setup WinXP and Ubuntu you need at least 2 partitions (third is recommended for Linux swap). In a dual-boot with Win7 and Ubuntu you need at least 3 (Win7 uses two partitions). If you have a correctly set dual-boot system you do not need a liveCD, you should be able to just boot and then given a menu to select Ubuntu or Windows.

1. How many windows versions do you have installed and what do you mean they will not boot.
2. the disk drive is fine, but the CD itself may be damaged. If you are trying to boot a Windows CD, then the CD may be damaged.
3. Read above on how many partitions are needed.
4. You can only run individual Windows programs in wine. You can never run an entire copy of windows. If you want to run an entire copy of windows, then use Virtual Box.
5. What CD do you have inserted, is it an Ubuntu liveCD or windows install CD or windows Upgrade CD. Are you sure the CD is bootable.
6. What keyboard are you using. There have been some issues reported with wireless keyboards and the boot menu. Tell us the model of your keyboard.
7. You can reformat the HDD with the Ubuntu LiveCD. Select "Try Ubuntu" and then go to System -> Admin -> Gparted. Note that reformatting will destroy all data on the HDD so BACKUP EVERYTHING IMPORTANT. However, once you reformat your HDD, any OS on it will be gone. You will have to install either Ubuntu or Windows.

Doing a clean reinstall of windows requires a Windows install CD. Then boot form the CD and go from there.


Thanks for this reply. 

I am trying to get rid of ubuntu and install windows again. i.e. install a clean copy of windows. 

I shut down the computer, put the windows disk in and click f11 on start up then click boot from cd. It just doesn't work for any of the 3 disks, is there any way of getting this to work?

I know there is no problems with the CD's or my disk drive so this rules out that problem. What else could be causing my system not to boot from a cd to install a clean copy of windows?

also ive tried another key board but still no joy. so doubt this is the problem. 

If there is no other way to get this working i will have to try number 7.

---

### Post by ledwardz on 2011-02-16
> **3Miro said:**
> Go to System -> Admin -> Gparted and you can reformat without the need to install anything. BACKUP EVERYTHING IMPORTANT FIRST.

by gparted u mean disk utility? or do i have  to install g parted. Sorry, i suck at this.

---

### Post by 3Miro on 2011-02-16
> **ledwardz said:**
> Thanks for this reply. 

I am trying to get rid of ubuntu and install windows again. i.e. install a clean copy of windows. 

I shut down the computer, put the windows disk in and click f11 on start up then click boot from cd. It just doesn't work for any of the 3 disks, is there any way of getting this to work?

I know there is no problems with the CD's or my disk drive so this rules out that problem. What else could be causing my system not to boot from a cd to install a clean copy of windows?

also ive tried another key board but still no joy. so doubt this is the problem. 

If there is no other way to get this working i will have to try number 7.

Booting from the CD or HDD is done at the level of the BIOS, which kicks in long before anything from Ubuntu has a chance to load. The BIOS will start Ubuntu only if you don't tell it to start from the CD or there is an issue with the CD. Your problem is with your CD device, the CD disk itself, they Keyboard or the BIOS.

- Make sure the key is F11 and not F12 or F1 or something else.
- Make sure the Windows CD is bootable. Some Windows disks come as "upgrade", which requires you to have older version of windows installed before you can install the new one. That is, some windows disks don't let you install a "clean" version of windows.
- Make sure your keyboard is working by entering the BIOS menu (careful making changes to the BIOS settings, if you don't know what you are changing you can badly damage your system beyond repair).

If you can boot from a Ubuntu LiveCD, your problem is with the Windows disk.

---

### Post by 3Miro on 2011-02-16
> **ledwardz said:**
> by gparted u mean disk utility? or do i have  to install g parted. Sorry, i suck at this.

If you are using a liveCD (and you should use that if you want to wipe the entire HDD), then Gparted is already installed in System -> Admin. If you have installed Ubuntu on your HDD, then you need to install Gparted from the Ubuntu Software Center. Note that if you have booted from your HDD, then you cannot reformat the entire HDD (just parts of it).

---

### Post by ledwardz on 2011-02-16
> **3Miro said:**
> Booting from the CD or HDD is done at the level of the BIOS, which kicks in long before anything from Ubuntu has a chance to load. The BIOS will start Ubuntu only if you don't tell it to start from the CD or there is an issue with the CD. Your problem is with your CD device, the CD disk itself, they Keyboard or the BIOS.

- Make sure the key is F11 and not F12 or F1 or something else.
- Make sure the Windows CD is bootable. Some Windows disks come as "upgrade", which requires you to have older version of windows installed before you can install the new one. That is, some windows disks don't let you install a "clean" version of windows.
- Make sure your keyboard is working by entering the BIOS menu (careful making changes to the BIOS settings, if you don't know what you are changing you can badly damage your system beyond repair).

If you can boot from a Ubuntu LiveCD, your problem is with the Windows disk.


okay i can boot from ubuntu live cd so surley there is no problem with the disk drive
ive also used vista cd to get ubuntu off my laptop a few days ago and to double check ive just used virtual box to install windows 7 ultimate which works no problem? so i don't think its a problem with my disk. Ive also entered the bios using the delete button on start up and went into advanced bios settings then selected my cd draw as the primary boot so it's not my key board either?

---

### Post by ledwardz on 2011-02-16
If there is nothing else it can be i am going to have to try number 7. Reformat the whole hard drive and install windows. Its my only option left i think. I will probably screw the whole computer in the process but its worth a go. 

In gparted is it as simple as clicking on the whole hardrive and reformat to ntfs?

---

### Post by Mark Phelps on 2011-02-16
Sounds like you've got some basic problems others just keep ignoring in their advice to you ...

1) Can't change the BIOS to boot from CD.  Telling you to boot from ANY CD is a waste of time until you can fix this.

2) Press any key (on screen) means that the BIOS has detected media in the drive, but your keyboard is getting ignored.  If it's a USB keyboard, make sure it's connected directly to the PC, not to a HUB. You may have to try different USB ports for the keyboard until you find one that works.

IF you have an older PC that has one of the old PS/2 keyboard/mouse connectors, you may have to obtain one of those keyboards to be able to get into the BIOS and change it.

---

### Post by 3Miro on 2011-02-16
> **ledwardz said:**
> okay i can boot from ubuntu live cd so surley there is no problem with the disk drive
ive also used vista cd to get ubuntu off my laptop a few days ago and to double check ive just used virtual box to install windows 7 ultimate which works no problem? so i don't think its a problem with my disk. Ive also entered the bios using the delete button on start up and went into advanced bios settings then selected my cd draw as the primary boot so it's not my key board either?

When you insert the windows CD, do you get a message:
```
Press any key to boot form the CD ...
```
which flashes for a few seconds?

---

### Post by ledwardz on 2011-02-16
> **3Miro said:**
> When you insert the windows CD, do you get a message:
```
Press any key to boot form the CD ...
```which flashes for a few seconds?


yeah i do. i click keys but it just keeps putting the dots (.....) maybe it could be the keyboard because its connected to a usb and not the other thingy that mark suggested?

---

### Post by 3Miro on 2011-02-16
> **ledwardz said:**
> If there is nothing else it can be i am going to have to try number 7. Reformat the whole hard drive and install windows. Its my only option left i think. I will probably screw the whole computer in the process but its worth a go. 

In gparted is it as simple as clicking on the whole hardrive and reformat to ntfs?

Gparted is "delete" partitions "create" partitions and "format" partitions. However, if you make everything NTFS you will not be able to boot anything. You will still have to install either Ubuntu or Windows.

---

### Post by 3Miro on 2011-02-16
> **ledwardz said:**
> yeah i do. i click keys but it just keeps putting the dots (.....) maybe it could be the keyboard because its connected to a usb and not the other thingy that mark suggested?

Keyboard issue. See if the keyboard can be connected in any other way and/or find another keyboard.

---

### Post by ledwardz on 2011-02-16
> **Mark Phelps said:**
> Sounds like you've got some basic problems others just keep ignoring in their advice to you ...

1) Can't change the BIOS to boot from CD.  Telling you to boot from ANY CD is a waste of time until you can fix this.

2) Press any key (on screen) means that the BIOS has detected media in the drive, but your keyboard is getting ignored.  If it's a USB keyboard, make sure it's connected directly to the PC, not to a HUB. You may have to try different USB ports for the keyboard until you find one that works.

IF you have an older PC that has one of the old PS/2 keyboard/mouse connectors, you may have to obtain one of those keyboards to be able to get into the BIOS and change it.

Thanks, i will give this a go and it is a old computer with the PS/2 ports. I also now have 2 keyboards connected to different usbs so don't think it will be the usb ports.

---

### Post by grahammechanical on 2011-02-16
Am I understanding you correctly? You want to get rid of Ubuntu completely and you are asking for help to do that on a Ubuntu forum! What is wrong with the Microsoft forums? It is their discs that refuse to work. Is it not?

---

### Post by ledwardz on 2011-02-16
> **3Miro said:**
> Keyboard issue. See if the keyboard can be connected in any other way and/or find another keyboard.

Thanks for your help, if it has been the key board causing me weeks of pain i'm going to be extremely angry.

---

### Post by ledwardz on 2011-02-16
> **grahammechanical said:**
> Am I understanding you correctly? You want to get rid of Ubuntu completely and you are asking for help to do that on a Ubuntu forum! What is wrong with the Microsoft forums? It is their discs that refuse to work. Is it not?

i want to install windows and then dual boot with ubuntu. Its easier to do this from windows.

also i have converted more people to ubuntu than enough so shut up.

---

### Post by ledwardz on 2011-02-16
> **3Miro said:**
> Keyboard issue. See if the keyboard can be connected in any other way and/or find another keyboard.

Yeah that worked. I cnt believe it was something as simple as that..... Your genious. Thanks.

---

