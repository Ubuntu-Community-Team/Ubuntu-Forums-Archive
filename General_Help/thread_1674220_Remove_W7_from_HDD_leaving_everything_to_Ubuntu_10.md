---
title: "Remove W7 from HDD leaving everything to Ubuntu 10.10"
date: 2011-01-23
forum: General Help
---

### Post by xic816 on 2011-01-23
How can I remove w7 starter from my HDD leaving everything for Ubuntu?

Se picture..


[IMG]http://file:///home/mssm90/Pictures/Screenshot.png[/IMG]

I'm using Gparted as you can see.
Guessing sda 1 and 3 = w7, sda 4 = recovery and sda 2 = linux?

How do i proceed?

(I don't know if it matters but I installed ubuntu via w7)

Thanks for reply

---

### Post by ajgreeny on 2011-01-23
It looks as if this is a wubi install of ubuntu inside windows, so it is not very straightforward to do what you want.

Have a good read through of the wubi megathread in my signature, but you may decide it is just easier and quicker to start from scratch, now you know that the hardware works OK, and do a clean install to a properly partitioned system.

---

### Post by xic816 on 2011-01-25
> **ajgreeny said:**
> It looks as if this is a wubi install of ubuntu inside windows, so it is not very straightforward to do what you want.

Have a good read through of the wubi megathread in my signature, but you may decide it is just easier and quicker to start from scratch, now you know that the hardware works OK, and do a clean install to a properly partitioned system.

First off, thanks for replay!
Second, When I try to install ubuntu through bios (USBpenn -> use eeepc)
I cant manage to get through the installation. When I get to this step;

3. Prepare to install Ubuntu: We recommend you plug your computer into a  power source for this stage. You should also make sure you have enough  space on your computer to install Ubuntu. We  advise you to stay  connected to the Internet so you can get the latest updates while you  install Ubuntu. If you're having problems connecting to the Internet,  use the menu in the top-right hand corner to select a network.

When clicking the next button it just starts loading (loading icon) that's it... It don't move on to the next step for some reason, please advice.

---

### Post by Bucky Ball on 2011-01-25
Welcome. 

How long are you waiting?

Another option is to boot from the CD, 'Try Ubuntu', open Gparted in the desktop and kill the Windows install, then install Ubuntu. You could omit the 'kill Windows partitions' part and just install and kill them during the partitioning section.

---

### Post by xic816 on 2011-01-25
> **Bucky Ball said:**
> Welcome. 

How long are you waiting?

Another option is to boot from the CD, 'Try Ubuntu', open Gparted in the desktop and kill the Windows install, then install Ubuntu. You could omit the 'kill Windows partitions' part and just install and kill them during the partitioning section.


I'm talking 1-2hours and it's suppoused to go instantly.

How can I kill W-install? Do u mean try ubuntu -> delete everything -> install ubuntu?
The thing is I cant install ubuntu via ubuntu test (same problem occur) and the other 
thing is that I can't choose anything while installing it through wubi.

Just read something about ubuntu installation and SATA hdd is not corresponding so
something should be written in kernl or something?!

---

### Post by wilee-nilee on 2011-01-25
Are you booting to the live desktop to make sure the pendrive is loaded with a good ISO download?

When you power on the computer to boot the thumb hold down the shift key and use that menu to check the thumb, and to get to the try Ubuntu live desktop.

---

### Post by xic816 on 2011-01-25
> **wilee-nilee said:**
> Are you booting to the live desktop to make sure the pendrive is loaded with a good ISO download?

When you power on the computer to boot the thumb hold down the shift key and use that menu to check the thumb, and to get to the try Ubuntu live desktop.


If you are asking about the condition of ubuntu on the pendrive then yes It works fine
in test mode. What I have tried regarding pendrive;

- Make it bootable after ubuntus instructions 
+ In windows
+ In Ubuntu
- change 10.10 64bit -> 32bit
- change 10.10 -> 10.04
- change the "make usb bootable" app.

All the same...

But I got one small error if rebooting while in test mode;
The error message looks like this;

[33872.146177] end_request: I/0 error, dev sda, sectro 448392
[33872.147802] end request I/0 error, dev sda, sector 448392
[33872. 14........

PS: I have also run a sys.check on the pendrive and it passed

FYI: I have installed ubuntu on 2 of my computers (stationary and netbook) via Windows - wubi and it works fine.

I didn't quite understand what you means by thumb..shift key please explane

---

### Post by wilee-nilee on 2011-01-25
Holding down the shift on powering on brings up a early menu, can you boot to the live desktop, with this thumb?

If so you can open system-admin-gparted and delete all that is on the HD, then choose the install from the desktop icon.

---

### Post by akand074 on 2011-01-25
You could try doing a manual install. Just select that and then it will open up a partition manager. Delete all the partitions then 

> 1. Delete the entire drive/every partition you have so that all you have left is just one big block of unallocated space.
2. a) If you don't want a separate partition for /home (config files and  your data) make a new partition equal to the size of the entire drive  minus the amount of RAM you have. Set it as type EXT4, Primary  partition, beginning, choose to format, and give it a mount point of  "/".
   b) If you do want a separate partition for /home then do the same  thing as step A except just make the partition around 20GB-40GB, and  then make a new partition with all the space you have left minus the  amount of RAM you have and give it all the same settings except mount  point of "/home".
3. Make a new partition with the amount of unallocated space you have  left ~= to the amount of RAM you have and set it as "swap" and that's  all you have to do for that one.
4. There will be a drop down menu asking where to install GRUB, it  should automatically be on your only hard drive.. just make sure it is.
5. Click next and let the installer do it's thing. Once it's done you  shouldn't have any problems, I have suggested this to another person  before and it solved his issue with GRUB.. though he might have had two  hard drives.. I can't remember.


I just copied that from a post I made on another thread.. see if that gets through the install.

---

### Post by xic816 on 2011-01-25
> **wilee-nilee said:**
> Holding down the shift on powering on brings up a early menu, can you boot to the live desktop, with this thumb?

If so you can open system-admin-gparted and delete all that is on the HD, then choose the install from the desktop icon.

Yeah tried that, It woun't install from ubuntu testing mode!
It's just loading at step 3...

---

### Post by xic816 on 2011-01-26
Just tested the usb penn on my frnds computer and the same thing happend which means it's only the usb-penn.

Any clue what I did wrong tho? 
USed the guidlines at ubuntu.com for both ubuntu and windows
[LEFT]The usb penn: DT101 G2 4gb kongston
[/LEFT]

---

### Post by wilee-nilee on 2011-01-26
> **xic816 said:**
> Just tested the usb penn on my frnds computer and the same thing happend which means it's only the usb-penn.

Any clue what I did wrong tho? 
USed the guidlines at ubuntu.com for both ubuntu and windows
[LEFT]The usb penn: DT101 G2 4gb kongston
[/LEFT]

So we never really got to how you loaded the thumb, if you haven't used unetbootin then try it .
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Reformat the thumb and reload it, I have had cd's and thumb's not work when every test say they should.

---

### Post by xic816 on 2011-01-27
> **wilee-nilee said:**
> So we never really got to how you loaded the thumb, if you haven't used unetbootin then try it .
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Reformat the thumb and reload it, I have had cd's and thumb's not work when every test say they should.

When trying to install it i just got to step 3, it's the step where u choose to install uppdates and third party application/uppdates. 

Yeah i have tryed the unetbootin tool.

The thing is that the usb worked while installing it through wubi! which means it's something with the usb penn and booting?!
Is there like requirements for the usb to be able to be bootable? 

(When u say thumb do u mean the pendrive/usb right?)

---

### Post by xic816 on 2011-01-27
Okey I'm trying again...

I just downloaded unetbootin for ubuntu/linux and 7z file, 
When im trying to add iso i says it cant find it so decided to 
just download it through the programm 3 options appear;
1. ubuntu 10.10 hdmedia 
2. -"- live
3. -"- netinstall
Which one should I choose and should i refomat the usb penn before proceeding
if so, which filesystem?

Thanks

---

### Post by xic816 on 2011-02-01
I figured it out, it was the USB-penn!

---

