---
title: "Installing Lubuntu"
date: 2012-04-03
forum: General Help
---

### Post by bOgNeR17 on 2012-04-03
Is it possible to install Lubuntu without the need for a USB or a CD/DVD. I just want to download the iso and install it from there?

---

### Post by flurospar on 2012-04-03
Yes, with Unetbootin [ [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) ], provided you have an existing OS already installed on the comp.

In the Unetbootin window select "Hard disk" as the drive type and point it to the ISO and the proper hard drive.

Reboot, and you shall get options to boot into "Unetbootin". Boot into it, and you can then install it as you would do with a Live CD (but remember not to format the very partition in which Unetbootin has placed the contents of the ISO. IOW, You shouldn't erase the partition you selected in the Unetbootin screen.)

---

### Post by bOgNeR17 on 2012-04-03
Well I am currently using Linux Mint 12 LXDE and I would like to switch to Lubuntu, so would it be possible to first install Lubuntu and then delete the Linux Mint?

---

### Post by searchfgold6789 on 2012-04-03
Yes, after Lubuntu is finished installing, start the Disk utility. Use it to delete your Linux Mint partition, open up a Terminal and run ```
sudo update-grub
```

---

### Post by bOgNeR17 on 2012-04-03
Thank you for your help, last question how do I install Unetbootin ?

---

### Post by raja.genupula on 2012-04-03
open your terminal do this 

```
sudo apt-get install unetbootin
```

it will installs.

---

### Post by bOgNeR17 on 2012-04-03
Done that, now could you please tell me how to run unebootin?

---

### Post by bOgNeR17 on 2012-04-03
Anyone :confused:

Found it out myself just typed " unetbootin" into the terminal and it loaded unetbootin up. Thanks for the help.

---

### Post by bOgNeR17 on 2012-04-03
I configured it all but for some reason when I reboot the computer it does not give me an option to boot using unetbootin.

---

### Post by jerome1232 on 2012-04-03
unetbootins bootloader is probably on the other drive, set the correct drive as the main boot drive from your bios.

Most sytems will flash a message at you during bootup to hit f2 or esc or del to get into the bios (just look for the message), you'll have to find it in the menu's from there as bios screens vary from computer to computer.

---

### Post by bOgNeR17 on 2012-04-05
Okay I restarted the system, pressed F2 and I went to advance settings I could not see anything to do with Unebootin, all I could see was Realtek Booter, Hard Disk, the name of the Disk Drive and a floppy drive which I don't have.

---

### Post by bOgNeR17 on 2012-04-05
Problem sorted got myself a USB pen followed the same procedures and and then select USB HDD from the boot menu. Thanks for the help:KS

---

### Post by bOgNeR17 on 2012-04-05
Actually could anyone explain to me how to install ArchLinux along with Lubuntu. Also would it make any difference to the performance of my computer having both of the OS's on my computer?

---

### Post by Fwission on 2012-04-05
> **bOgNeR17 said:**
> Actually could anyone explain to me how to install ArchLinux along with Lubuntu. Also would it make any difference to the performance of my computer having both of the OS's on my computer?

I'm not sure if you are experienced enough to install arch. Arch requires that installation is done more manually. I suggest you try to install it first on virtual box to see if you can preform the steps.

However, if you are adamant to install Arch I can explain

EDIT: Besides using up hardrive space, Arch Linux will probably run better than lubuntu but its a lot more work to set-up (talking hour(s))

---

### Post by bOgNeR17 on 2012-04-05
Could you explain how to install it on virtual box first please and I will take it from there?

---

### Post by Fwission on 2012-04-05
> **bOgNeR17 said:**
> Could you explain how to install it on virtual box first please and I will take it from there?

First head over to the arch Linux website to download your ISO based off of your architecture ([http://www.archlinux.org/download/](http://www.archlinux.org/download/))

Install virtual box:

[CENTER]```
sudo aptitude install virtualbox
``` 
or 
```
sudo apt-get install virtualbox
```[/CENTER]

open virtualbox and set-up a new machine, follow the reccomended steps and if you get stuck attach a picture with your question (going off memory, running Linux off my portable USB)

---

### Post by bOgNeR17 on 2012-04-05
Okay thank you Fwission.

---

