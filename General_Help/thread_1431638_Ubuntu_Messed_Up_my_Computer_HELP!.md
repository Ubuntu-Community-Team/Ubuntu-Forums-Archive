---
title: "Ubuntu Messed Up my Computer HELP!"
date: 2010-03-16
forum: General Help
---

### Post by dvd.marc.12 on 2010-03-16
ok, so i was trying to install Ubuntu 9.10 on my usb stick so i booted with a live cd and went through the installation process. I made sure i installed it to my usb stick, and the installation went without a hitch. so i wanted to use windows, so i took out the USB stick and turned my computer on. then i see:

Grub loading.
error: no such disk
grub rescue>_

So then I put in my usb stick and rebooted, and grub loaded, and I got to choose to either boot to ubuntu or Windows vista.

SO WHY IS GRUB ON MY COMPUTER AND HOW DO I GET RID OF IT!!!! i just want to boot normally into windows! :(

---

### Post by mjitkop on 2010-03-16
> **dvd.marc.12 said:**
> ok, so i was trying to install Ubuntu 9.10 on my usb stick so i booted with a live cd and went through the installation process. I made sure i installed it to my usb stick, and the installation went without a hitch. so i wanted to use windows, so i took out the USB stick and turned my computer on. then i see:

Grub loading.
error: no such disk
grub rescue>_

So then I put in my usb stick and rebooted, and grub loaded, and I got to choose to either boot to ubuntu or Windows vista.

SO WHY IS GRUB ON MY COMPUTER AND HOW DO I GET RID OF IT!!!! i just want to boot normally into windows! :(

I am far from being an expert with Ubuntu but my understanding is that GRUB gets installed automatically when you install Ubuntu. It seems to me that GRUB may have been installed on your USB stick when you installed Ubuntu.

That's the short explanation about your problem. Somebody with more experience will need to help you fix it because I don't have the knowledge.

Good luck.

---

### Post by dvd.marc.12 on 2010-03-16
thanks for the reply, BUT I NEED HELP QUICK!!!!! and please talk in explain because i am new to linux
PLEASE!!!!!!!!

---

### Post by ManyuX95 on 2010-03-16
Well yeah, the problem is that you need grub to enter Ubuntu, so I thhink that first: you should have installed it as an app on windows 2: you should have informed yourself first and 3: It is an almost necesary thing to backup your data when you are going to try something strange or new to you :S I hope you can get pro help because everyone has passed by something like that :D Luck!

---

### Post by mechro on 2010-03-16
The default installation is to install Grub to the Master Boot Record of your main hard drive. If you only wanted Grub on the USB stick there is an "Advanced" button option during the install. Perhaps the Ubuntu installation process doesn't make this clear?

To restore your Windows bootloader you'll need a Windows CD or some other recovery tool. Have you got a Windows CD?

---

### Post by dvd.marc.12 on 2010-03-16
I have a windows cd, but i don't know what to do with it

I have tried fixmbr, but it doesn't reconize it as a command

can you direct me step by step to restore this MBR

---

### Post by mechro on 2010-03-16
What version of Windows are you using?

---

### Post by prodigy_ on 2010-03-16
This is why I hate Windoze junkies - they're always yelling.
/sigh

To OP:
Dude, it's not a Windoze forum in case you haven't noticed

---

### Post by dvd.marc.12 on 2010-03-16
Vista

---

### Post by dvd.marc.12 on 2010-03-16
to prodigy_

i am posting it here because i know it has something to do with linux and i just need help :(

and sorry i am yelling, i'm just really fustrated

---

### Post by mechro on 2010-03-16
I can't give you step-by-step cos I don't use Windows but the instructions are here...

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

By the way, if you're not sure what to do, take your time, ask more questions. You can still boot Windows with the USB stick inserted so don't panic.

I'm off now. Good Luck.

---

### Post by derekeverett on 2010-03-16
You can boot from the Windows Recovery Disk and restore windows. But be careful to choose "Fix Windows" if you don't want to wipe out your hard drive and everything on it.

If you want to do a fresh install I would boot from the usb stick and use GRUB to get into Windows and then backup your important documents.

In the future if you want to dual boot between Windows and Ubuntu I would recommend installing Ubuntu with Wubi. That way you can still use the Windows boot loader if that's what you prefer.

For the time being.. is booting of the USB stick and putting up with GRUB that big of a problem? It's better than making hasty decisions and messing your system up further, in my opinion anyway.

Hope that helps...

---

### Post by julio.tomaschitz on 2010-03-16
Well, you did this: installed the system in your usb stick  but the grub instalation were to the MBR. 
I really dont know how to solve it, unless backing up everything and format again.
Next time try pendrive linux: [www.pendrivelinux.com](www.pendrivelinux.com) 
There is a program called universal usb installer, you just need this little program, and the ubuntu.iso (better if they could be in the same folder). Just follow the instructions and configure your BIOS.

I'm sorry for you problem, but I'm sure there is another way to solve it without losing your data and your patience :)

---

### Post by morpheus_017 on 2010-03-16
Start booting from vista installation disk. Select "Windows Setup" and press enter. After some time select your language and press "next". Press "Repair your computer". after some time press "no" and "next". select command-line. when the cmd window was opened replace %YOUR_CD_LETTER%, enter command and press enter.
```
%YOUR_CD_LETTER%:\boot\bootsect /nt60 All
```
then enter "exit" and press reboot. Bootmanager was fixed.


PS sorry for my english.

---

### Post by afmGM on 2010-03-16
Try to use EasyBCD to restore the Vista boot loader.  Just boot into Windows Vista, and install this:

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

after that launch it, and go to Manage Bootloader, select Reinstall Vista Bootloader, then "Write MBR".  Make sure to back up all your data first, there's a small chance something might go wrong.

Sorry about your bad experience with Ubuntu.

Edit: As others might of said, using the Windows disk would be the best and safest choice probably.

---

### Post by uRock on 2010-03-16
If you install the Lilo boot loader, it will repair the Master Boot Record so well you will not be able to tell grub was ever there. To install Lilo and let it work its magic, enter these two commands into a terminal while botted into the LiveCD.```
sudo apt-get install lilo
```
```
sudo lilo -M  /dev/sda mbr
```

---

### Post by dvd.marc.12 on 2010-03-16
thanks for all the help guys, i ended up fixing in by putting bootrec.exe /fixmbr and /fixboot

---

### Post by arnelsmith on 2011-03-22
I think your Usb have problem, Thats why they cant save it.....

---

