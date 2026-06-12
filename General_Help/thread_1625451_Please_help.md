---
title: "Please help"
date: 2010-11-19
forum: General Help
---

### Post by Costigan67 on 2010-11-19
Sorry guys if this is in the wrong place but I'm badly needing some help.

I'm just after installing Ubuntu 10.10 and when it asked me to restart I got to the screen where you can 'press F2 to enter settings, etc' and after that I just get a blank black screen.... Nothing. I installed Ubuntu alongside Windows 7 but it doesnt even give me a choice of operating system to load, its just black screen. 

I'm currently typing by booting from usb and using the 'Try Ubuntu' mode.

I went to install again but the option 'Install alongside operating sytem had gone', I know windows 7 is still here somewhere though because I can view the file system, I just can't get an OS to load up!!

Please can someone help??

Thanks for reading.

---

### Post by dino99 on 2010-11-19
use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by Costigan67 on 2010-11-19
> **dino99 said:**
> use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

I really appreciate the quick reply mate but that's all greek to me, could you break it down and simplify it a bit? 

Thanks

---

### Post by dino99 on 2010-11-19
take time to read and understand before doing :)

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

more info following links below

---

### Post by Costigan67 on 2010-11-19
> **dino99 said:**
> take time to read and understand before doing :)

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

more info following links below

I'm by no means a computer expert but I read and done everything I was prompted to do. Just when I start my laptop no OS will boot, just a black screen. 

Can you, or anyone else, shed any light on it?

---

### Post by mastablasta on 2010-11-19
do you get to a menu where you choose your OS? if not then the problem is that GRUB (which is the Ubuntu bootloader) doesn't load. maybe it's a bad install. did you check the md5sum of you liveUSB before starting the install?
 
It could be grub got installed in the wrong place.
 
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by Quackers on 2010-11-19
Please boot from the live cd and choose "try ubuntu" then go to the site below and download the boot script to your DESKTOP then open a terminal and run the command given on the first page of that site. This will produce a results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags in your next post. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Rubi1200 on 2010-11-19
+1 to the advice posted by Quackers.

The boot info script will generate information that could be essential in helping us diagnose the problem as well as make offering solutions easier.

Please also post the computer specifications, especially RAM and graphics card.

Thanks.

---

