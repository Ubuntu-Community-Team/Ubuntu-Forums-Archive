---
title: "Windows on ubuntu?"
date: 2012-08-09
forum: General Help
---

### Post by n123q45 on 2012-08-09
hey i'm a modder and id like to use my modding programs on ubuntu. the only problem is that they are in the .exe format. they are windows programs. is there any way i could open them? ive already tried wine. .

---

### Post by SeijiSensei on 2012-08-09
I don't know what being a "modder" means, but you can run Windows in a virtual machine using [VirtualBox]("http://www.virtualbox.org/").

---

### Post by n123q45 on 2012-08-09
i tried that. it just gives me an error saying "no bootable mediaum found. system halted"

---

### Post by GreatDanton on 2012-08-09
You have to set up from where VM will boot (ISO file).

---

### Post by n123q45 on 2012-08-09
where could i get an windows xp iso. free

---

### Post by papibe on 2012-08-09
I don't think there's such thing.

You may want to downloading the [Windows 8 Release Preview]("http://windows.microsoft.com/en-US/windows-8/download/") from Microsoft.

Regards.

---

### Post by GreatDanton on 2012-08-09
oops my mistake. I think you can install windows without iso file.

---

### Post by n123q45 on 2012-08-09
> **GreatDanton said:**
> oops my mistake. I think you can install windows without iso file.

how?

---

### Post by uRock on 2012-08-09
> **papibe said:**
> I don't think there's such thing.

You may want to downloading the [Windows 8 Release Preview]("http://windows.microsoft.com/en-US/windows-8/download/") from Microsoft.

Regards.

+1 

There is no legal means for getting a free copy of Windows XP.

---

### Post by n123q45 on 2012-08-09
> **uRock said:**
> +1 

There is no legal means for getting a free copy of Windows XP.

k

---

### Post by QIII on 2012-08-09
To install Windows in VirtualBox, you need a legal, licensed retail copy of Windows.

A Windows "recovery" dist will not work.

And don't use this forum to ask how to get a pirated copy.

---

### Post by hansum_rahul on 2012-08-09
Is the .exe file by any chance 16-bit DOS type program?

In that case, Doxbox would be your best bet!

Again, what error does wine give?

---

### Post by Cheesemill on 2012-08-09
Another option is that *some* .exe files can be run natively using Mono, but this only works if the software is written usinga certain type of .NET

---

### Post by Kalanac on 2012-08-09
Have you double checked WineHQ's app database for the software you are using?

[http://appdb.winehq.org/](http://appdb.winehq.org/)

It provides details of little tricks and workarounds that can get programs to work in WINE, just search for the relevant software and check the ratings.  Anything Platinum or Gold rated should work with little or no fiddling about.  Silver needs some amount of tech jiggery-pokery, Bronze you can maybe get the program to limp along with some odd errors and a lot of fuss.  Garbage means it just won't run.

---

### Post by coldraven on 2012-08-09
> **QIII said:**
> To install Windows in VirtualBox, you need a legal, licensed retail copy of Windows.

A Windows "recovery" dist will not work.

And don't use this forum to ask how to get a pirated copy.

A Windows recovery disc will work if it is the one that came with your PC.
You have to configure VirtualBox's fake BIOS to contain the strings that the disc is looking for otherwise XP will not activate.
Search the VBox forums for the topic found here:
[https://www.virtualbox.org/manual/ch09.html#changedmi](https://www.virtualbox.org/manual/ch09.html#changedmi)

---

### Post by Mark Phelps on 2012-08-09
> **coldraven said:**
> A Windows recovery disc will work if it is the one that came with your PC.
Depends entirely on WHAT the OP is trying to do and what else they have to use ...

If they are trying to erase the entire drive and reinstall Windows from scratch, IF the recovery disk is one of those that contains the compressed Windows image, that will probably work.  

If, as is more often the case, it only boots into a restore program -- that then searches the hard drive for the saved compressed Windows image -- if it does not find that image, it will NOT do the restore.

If all they are trying to do is install Windows, in a dual-boot kind of setup, then NO, a recovery disk will not do that.

---

### Post by directhex on 2012-08-09
> **uRock said:**
> +1 

There is no legal means for getting a free copy of Windows XP.

Strictly speaking, if you have a license for Windows 7 Pro or higher, then you also get access to XP for free, via the "XP Mode" facility in those versions of 7.

---

### Post by QIII on 2012-08-09
> **coldraven said:**
> A Windows recovery disc will work if it is the one that came with your PC.
 
Perhaps I should have said "... won't work legally."
 
"...came with your PC." A key thing that.  "Came with" can mean a couple of things
 
If it's a full install disk with a license sticker on the disk's container, it will work.  You used to get one when you bought a machine -- but it was often an OEM disk.  If the sticker is on the computer case, however, that's where Windows has to go. See OEM disks below.
 
If it's a recovery disk with the license on the disk's case and it does not say "For distribution with new Belchfire computers only", it ***may** *work provided all the DMI entries are correct.   If the sticker is on the computer case, however, that's where Windows has to go.  See OEM disks below.
 
If it's a recovery disk you made, see OEM disks below.  If the sticker is on the computer case, however, that's where Windows has to go.
 
On OEM disks:  The EULA from both the OEM and Microsoft generally contains verbiage expressly forbidding the use of an OEM disk to install the OS in a virtual machine.  If that is the case, will be violating the EULAs.

---

### Post by coldraven on 2012-08-09
> On OEM disks:  The EULA from both the OEM and Microsoft generally  contains verbiage expressly forbidding the use of an OEM disk to install  the OS in a virtual machine.  If that is the case, will be violating  the EULAs.

Well I don't want to get into a big discussion because TBH I will not be buying or using MS products in the future if at all possible.
In my case this laptop came with a XP HP OEM disc with no number on it. Even if I tried to install it using the MS activation code on this laptop it would not work because this machine was sold by HP as a "downgrade" from Vista Business and the serial is not recognised.
As for the EULA, I have not seen it and under British law I think that MS would fail to prevent me using one copy of the software that I purchased, on the machine that it was sold with, virtual or not.

Sorry to have wandered off the OP's topic but as you can tell I am angered at having to pay the "MS Tax".

---

### Post by uRock on 2012-08-09
> **directhex said:**
> Strictly speaking, if you have a license for Windows 7 Pro or higher, then you also get access to XP for free, via the "XP Mode" facility in those versions of 7.

We do not support the illegal use of any Windows product. Last I looked Windows 7 Pro with license wasn't up for free downloads on Microsoft's site. 

Please do not derail this thread any further.

Thanks,
uRock

---

