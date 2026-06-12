---
title: "Boot loader and the menu"
date: 2006-03-07
forum: General Help
---

### Post by raha on 2006-03-07
Hi.
I installed Vista on my system but I forgot that Win Vista cant recognise Ubuntu partition, so I can start up my Ubuntu.
I really want to fix this without reinstalling the whole Ubuntu again,
Can anybody help?

thanks

---

### Post by o_fortuna on 2006-03-07
[QUOTE=raha]Hi.
I installed Vista on my system but I forgot that Win Vista cant recognise Ubuntu partition, so I can start up my Ubuntu.
I really want to fix this without reinstalling the whole Ubuntu again,
Can anybody help?

thanks[/QUOTE]
There's something in the wiki about this: [RecoveringUbuntuAfterInstallingWindows]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28recovering%29")

It should work, even for Vista. You can reinstall Grub without damaging either partition (but always back up data!)

---

### Post by raha on 2006-03-07
Thanks dude, I am going to try this.

---

### Post by raha on 2006-03-07
Oh, by the way, I am using DapperDrake and do you know from where I can download the live CD ? because it says I need a live CD.

Thanks

---

### Post by Xian on 2006-03-07
[QUOTE=raha]I am using DapperDrake and do you know from where I can download the live CD ?[/QUOTE]

[Dapper Download Methods and Links](http://cdimage.ubuntu.com/releases/dapper/flight-4/)

---

### Post by raha on 2006-03-07
Thanks a millions

---

### Post by raha on 2006-03-07
IS there any easier way to fix this issue ?
I messed some stuff up and I dont think I can fix it like this :(

---

### Post by Xian on 2006-03-07
You can use the InstallCD...

Boot the system with the InstallCD in the drive.
At the boot options line type:

rescue

Then after that loads, mount the applicable partition.
Next execute the grub install command:

# grub-install /dev/hda1

You may of course need to change the partition number.
Then check to make sure your /boot/grub/menu.lst is correct.

---

### Post by raha on 2006-03-07
[QUOTE=Xian]
Then after that loads, mount the applicable partition.
Next execute the grub install command:

# grub-install /dev/hda1

You may of course need to change the partition number.
Then check to make sure your /boot/grub/menu.lst is correct.[/QUOTE]

Thanks for answer.
How do I mount the applicable partition ?

thanks

---

### Post by Xian on 2006-03-07
This is right out of the wiki:

* When the Ubuntu splash screen comes up with the boot: prompt, type in rescue and press enter. 

* Choose your language, location (country) and then keyboard layout as if you were doing a fresh install. 

* Enter a host name, or leave it with the default (Ubuntu). 

* At this stage you are presented with a screen where you can select which partition is your root partition (there is a list of the partitions on your hard drive, so you are required to know which partition number Ubuntu is on). This will be dev/discs/disc0/partX , where the X is a partition number. 

* You are then presented with a command prompt (a hash). 

* type $ grub-install /dev/hdaX (where X is your Ubuntu root install).

=========

Or, if you want it sent (which is your case) to the MBR:
* type $ grub-install /dev/hda (where hda is the name of the drive).

---

