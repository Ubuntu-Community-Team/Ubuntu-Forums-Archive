---
title: "Choose whether/where to install Grub"
date: 2009-10-18
forum: General Help
---

### Post by ellaivarios on 2009-10-18
Hi everyone, this is my first post and I am also relatively new to Linux, although I had my first taste years ago when I was a university student, so bear with me please.

(Skip to this paragraph if you are bored - to get to my question)
I have tried the ubuntu live usb and I think ubuntu is great, so I decided to start using it, in fact I can't wait for the new version. I have a Dell laptop with a triple boot using windows xp, windows vista, and windows 7. I have created the two partitions necessary to install ubuntu, one for the OS and one for the swap/hybernation data.

I have downloaded the desktop cd and the alternate cd versions of ubuntu. Which one should I use if I am to not install grub in the master boot record? I want to install grub to the partition that ubuntu will be installed. How can I do this? Can someone give me specific instructions please? (I have my reasons for doing this)

I will chainload grub from the windows bootloader.

Thank you in advance.

---

### Post by zvacet on 2009-10-19
You can install Ubuntu with live Cd or alternate CD.All I found about Windows bootloader is [this.]("http://neosmart.net/wiki/display/EBCD/Ubuntu")Maybe someone else can be more helpful to you.

---

### Post by mike555 on 2009-10-19
Be careful, the button to install grub to the same partition is kinda small , it's called "advanced" just before the install ........push it and it will let you choose the partition to install grub to....

---

### Post by P4man on 2009-10-19
> **ellaivarios said:**
> Hi everyone, this is my first post and I am also relatively new to Linux, although I had my first taste years ago when I was a university student, so bear with me please.

(Skip to this paragraph if you are bored - to get to my question)
I have tried the ubuntu live usb and I think ubuntu is great, so I decided to start using it, in fact I can't wait for the new version. I have a Dell laptop with a triple boot using windows xp, windows vista, and windows 7. I have created the two partitions necessary to install ubuntu, one for the OS and one for the swap/hybernation data.

I have downloaded the desktop cd and the alternate cd versions of ubuntu. Which one should I use if I am to not install grub in the master boot record? I want to install grub to the partition that ubuntu will be installed. How can I do this? Can someone give me specific instructions please? (I have my reasons for doing this)

I will chainload grub from the windows bootloader.

Thank you in advance.

You can only have one MBR on a single drive (assuming you have just 1 drive). If you install ubuntu from either cd, it will install grub, and grub will be configured to boot all the other OSs. However, Ive read quite a few posts of people having > 1 windows installed, only one of them would work properly with grub. No doubt this can be fixed, but I thought Id warn you.

---

### Post by ellaivarios on 2011-06-20
Hi everyone. I started this thread nearly three years ago when I was oblivious to much of Linux, and although I am still oblivious, I have learned much.

If anyone wants more info on how this can be done, ask me in a personal message. I have mastered it, after destroying my system a few times and infinite patience. But experience makes perfect.

Essentially one can choose which bootloader to install in the Master Boot Record (MBR), whether it is Linux or Windows, and create items for the windows bootloader manually.

In my case, I have 5 partitions, each with an operating system. All are loaded with windows bootloader, which lists: 

Windows 7
Windows Vista
Windows XP
Macintosh Leopard
Ubuntu Linux

The Windows bootloader will take care of Vista and Win 7, and Win Xp can be booted using a program called EasyBCD to create an entry for the operating system in the bootloader pointing to the hard drive partition and the OS loaders.

With Linux it's easier. Upon Installation, as someone else pointed above in a reply, click on "advanced" just before clicking "Install" and after Gparted loads, choose where to install Linux, as well as where you want the Bootloader (Grub). The trick is to choose for the bootloader to be written in the same partition/drive as Linux, instead of the MBR, which would write over the Windows Bootloader. In turn, you can go into EasyBCD again and after creating an entry for Linux in the Windows Bootloader, you can tell the bootloader where to find Grub and Grub will take over from there once you select "Ubuntu Linux" in the previous Windows Bootloader menu I mentioned above that appears after booting the computer; Grub it will even have an option to go back to the Windows Bootloader.

There are many reasons someone may want to do this, instead of having Grub or Lilo. Especially if you want to virtualize a BIOS right from the MBR to create OEM compatibility for Windows or a number of other reasons.

---

