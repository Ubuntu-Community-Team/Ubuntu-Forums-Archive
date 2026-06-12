---
title: "Won't fully load"
date: 2011-01-22
forum: General Help
---

### Post by BrendanDM on 2011-01-22
I recently tried to run ubuntu on my laptop, I downloaded the desktop version, which said desktop and laptop on the download page, but I ran into a problem when I tried to load it. It will always load the Ubuntu title screen but messes up right after that, and this pops up [ATTACH]181758[/ATTACH]

I was able to run it on my actual desktop, but I hardly use it. My Laptop's specs are:

Model: Asus G60JX

Processor: Inter Core i5 M43 @2.27GHz

RAM: 4 GB

Video Card: NVIDIA GeForce GTS 360M

---

### Post by BrendanDM on 2011-01-22
is there a way to add the video driver to the install file? I'm thinking it could be a driver issue.

---

### Post by Quackers on 2011-01-22
Whilst booting from the cd and before the purple screen press the Esc key and a new screen will appear. Choose language and then choose the option to check the cd for errors.
If the cd checks out ok, press F6 and you should see more options bottom right. Try the "nomodeset" option and see if the disk will boot.
If that allows the disc to run and install Ubuntu you can then install available drivers from the desktop with System > Admin > Additional Drivers (which will probably run automatically).

---

### Post by BrendanDM on 2011-01-23
It did run automatically, but says that no proprietary driver are in use on my system. Should I try to download the driver?

---

### Post by Quackers on 2011-01-23
Which graphics card are you using?

---

### Post by BrendanDM on 2011-01-23
NVIDIA GeForce GTS 360M


Should be a chip I think

---

### Post by Quackers on 2011-01-23
Is performance ok without proprietary drivers?

---

### Post by BrendanDM on 2011-01-23
I can get it to display the GUI if I run it failsafe mode. I also noticed that now, if i don't go into the recovery mode option, it just comes up with the command line entry now. I already have it installed on my laptop.

---

### Post by Quackers on 2011-01-23
If you hold down the shift key during boot you should get a grub menu with the top Ubuntu item highlighted. Press the "e" key and with the down arrow move to the end of the line that says "quiet splash" then type a space then nomodeset then press ctrl + X to reboot. If the desktop loads ok you can then edit /etc/default/grub with ```
gksudo gedit /etc/default/grub
``` and after entering your password a new window will open in the text editor. Navigate to this line ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` and change it to look like ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```
Then save the file and exit the file. Then in the terminal run ```
sudo update-grub
```
This should enable a normal boot whilst you look for appropriate drivers.

---

### Post by BrendanDM on 2011-01-23
When I tried to save the file, I had to try using save as and replacing it, the save option was greyed ouy, and when i tried to replace it, i got an error saying I didn't have the permission to replace it.

---

### Post by Quackers on 2011-01-23
When saving the file did you click on FILE in the top bar and then save?
Did you use the guide above?

---

### Post by BrendanDM on 2011-01-23
i got it working on regular start up now, thanks for the help. But will I be able to download drivers for my video chip? when it was in fail safe mode, it went up to the resolution I wanted, but now it seems like it's stuck at 800*600

---

### Post by Quackers on 2011-01-24
I believe there have been some problems with the GT M series of cards, but that was some time ago. They may well be fixed by now. Maybe do some googling around. I suspect you may find something relevant.
I would be surprised if there are no users on here that have a similar card!
It may also be worth having a look in the Hardware & Laptops section of the forum.

---

### Post by BrendanDM on 2011-01-24
I got it working now. Thank you for all your help

---

### Post by Quackers on 2011-01-24
Oh good! How did you manage that? Others may benefit from what you did, thanks.

---

### Post by BrendanDM on 2011-01-24
> **Quackers said:**
> If you hold down the shift key during boot you should get a grub menu with the top Ubuntu item highlighted. Press the "e" key and with the down arrow move to the end of the line that says "quiet splash" then type a space then nomodeset then press ctrl + X to reboot. If the desktop loads ok you can then edit /etc/default/grub with ```
gksudo gedit /etc/default/grub
``` and after entering your password a new window will open in the text editor. Navigate to this line ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` and change it to look like ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```Then save the file and exit the file. Then in the terminal run ```
sudo update-grub
```This should enable a normal boot whilst you look for appropriate drivers.


This worked perfectly. The only problem I ran into was actually changing the grub file, which I had to take ownership of using ```
chown /YourUserNameHere grub
``` while in the correct directory. Luckily I was was able to save the file once I took ownership.

Then after it restarted, I enable the driver for my video chip in the additional driver menu and everything is perfect.

 Thanks again for your help. :p

---

### Post by Quackers on 2011-01-24
Excellent :-)
You're welcome!

---

