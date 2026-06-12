---
title: "Triple boot Win7 Ubuntu and JoliCloud with Grub2?"
date: 2010-11-30
forum: General Help
---

### Post by Daugusta12 on 2010-11-30
I have tried duel booting in the past, i have always wanted to try Linux, well the Ubuntu distribution specifically. But when ever i partitioned my drives and installed Ubuntu with Windows 7 i could never get the computer to boot correctly, i would always find a way to screw up the master boot record or something along those lines, end up formatting entirely and going back to windows. just a few days ago i formatted my computer's OS drive and installed Windows 7 64 Bit and Ubuntu 10.10 Alongside Windows with its own swap and root partition. I finally have a true dual boot without any issues. By the way, i LOVE Ubuntu, better then windows in almost every way in my opinion. Only reason i am keeping windows is for Windows media center(Watch TV though it) and for Microsoft Office. (Have a class at the moment where i need those applications and i cant use Google docs. And until this class is over and i get MythTV fully set up on my Ubuntu install i cant ditch windows just yet. However i also want to try JoliCloud, the Web based OS. And my question is this, Does anyone know if i use the windows installer within windows 7, will it mess up my boot loader, Grub 2 at the moment, or will it be added to GRUB2 boot menu? I have read that Joli uses Grub Legacy and i wanted to check in with some other folks before i take the plunge and potentially mess up my master boot record or Grub etc.

Any help would be greatly appreciated,
Cheers, Daugusta

---

### Post by sikander3786 on 2010-11-30
Hi. Welcome to the forums :-)

I haven't used Jolicloud so am not perfectly sure about everything I am going to say here.

1. Don't use the Windows/JoliCloud version, use the independent version instead as you are not using Windows bootloader but Grub2 at the moment.

2. If you are presented with an option during the install to install/not to install the bootloader, choose not to install it. As you said it is using Grub-Legacy, it might mess up your current dual boot. And if you choose not install the bootloader, running sudo update-grub from Ubuntu should add that to the current dual-boot Grub menu and make it triple-boot.

3. If anything goes wrong, you can simply restore your current Grub loader by following the 3 mentioned commands here.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Daugusta12 on 2010-11-30
Thank you very much, Ill let you know how it goes in a few hours, currently the Joli installer is downloading the OS and from reading someones post on Getsatisfaction.com During the installer, im guessing the next few steps after its done downloading the OS, it will detect my current OS's and install along side them, hopefully not messing up Grub2.

---

### Post by matt_symes on 2010-11-30
Hi

I am currently multi booting window 7, ubuntu 10.04, natty, fedora 14 (uses grub not grub2) and openSuse on my laptop. Some of the issues i have come across are that even if you can inform the installer not to install grub on the MBR, you will still have to boot into Ubuntu and update grub to find the new OS.

So in the best case scenario you don't install the new bootloader into MBR  but you have to run 

sudo update-grub

to see the new OS.

Worst case scenario you have to reinstall grub to the MBR using your LiveCD (as mentioned in the link by sikander), boot into Ubuntu and update grub.

Of course, you could have a dedicated boot partition and/or chain load. I have not bothered yet but will at some point.

Kind regards

---

### Post by sikander3786 on 2010-11-30
You are Welcome :-)

Which version are you downloading? I was talking about the one on this page named "Only Jolicloud".

[http://www.jolicloud.com/download](http://www.jolicloud.com/download)

And please let us know how that goes. It might be quite knowledge-able for someone else :-)

---

### Post by Daugusta12 on 2010-11-30
I was using the windows installer, witch was wrong, i cancelled that and now am downloading the ISO. Idk what i was thinking, the windows/Joli is basically Wubi for Ubuntu witch i dont want, thanks for the clarification on witch to use. I am downloading the ISO now, and will tell ya how it goes in a bit.

---

### Post by Daugusta12 on 2010-11-30
I Burned the .iso onto a disk, verified it and then booted into it. For some reason when i went to the partitioner step, the partitioner could not see any of my partitions on my main drive. Their was a button to create a new partition table, but i dont know what that does so i didn't touch it. Not sure if using it would remedy the situation, but unless that is the case, i guess ill try again when version 1.1 is released.

---

### Post by sikander3786 on 2010-11-30
If there is an option in your Bios, switch HDD mode to "ahci" or compatible and try again. Might be installer sees the partitions this time.

I am planning to try JoliCloud this weekend and will let you know how that goes.

---

### Post by jRdbRR on 2011-07-02
i found another thread with an answer to my question, thanks guys

---

