---
title: "Toshiba Lab Top No Longer Boots up?"
date: 2010-01-06
forum: General Help
---

### Post by Throbbing Gristle on 2010-01-06
[INDENT][COLOR=#990000]# sudo apt-get remove xorg-driver-fglrx[/COLOR]
[COLOR=#990000]# sudo dpkg-reconfigure -phigh xserver-xorg


I am guising at this point? It took for ever to boot up in 904 Jaunty. All though I never tried the above then and meant to. Thought the upgrade might get it . Now in Karmic Koala. I can get to the grub. Yet any fooling around here it always says unrecognized command. Well really I don't know what I am doing.

I have a Intel graphic processor in this lap top I am sure. When it did boot up in 904 the display would mess up. I had upgraded all the way from 804 because I could never get my Alfa usb wifi to work. As for now it will not boot up? Is there any links on the subject? Not sure why this in red it was not on purpose
[/COLOR][/INDENT]

---

### Post by Throbbing Gristle on 2010-01-06
If I type  help in the grub I get lots of choices which one . Which recovery choice do I make? There are six choices three recovery modes, and three non recovery modes. There are kernels 2.6.31-16 , 2.6.28-17 , 2.6.24-26 , then last memtest86+.

---

### Post by Throbbing Gristle on 2010-01-06
I also see root filesystem isn't mounted. General error mounting filesystems. Mountall seems to be failing? Then A maintenance shell will now be started , Control-D will terminate this shell and re-try. It just sits there? Any time I get to a command line I cannot log in as root ? If I type sudo I get Error 27: Unrecognized command. I have been looking for days now. This is not because I don't have the pass word it will not even go there. When ever I type in help there are lots of choices. Any help would be great as I am stumped. Thanks!

---

### Post by Throbbing Gristle on 2010-01-07
Wow what a joy a lonely thread! I put a live Kubuntu 910 cd in the computer. It wont even boot on that now. Ubuntu 910 broke my computer... Does this mean I got to buy a new hard drive now? It will not even acknowledge the cd burner now! Guess I will try the 804 Ubuntu to see what happens I have to download a new copy. It will not be long now looks like I will have 40 hours into this pig real nice..........

---

### Post by Throbbing Gristle on 2010-01-07
Ok further reading has shown me that all distros in 910 ubuntu will not ever support intel. Correct me if I am wrong. I am going to take a look at the 904 kubuntu I think to try something different. Will correct the grub etc as per instructions.

---

### Post by prem1er on 2010-01-07
I have no idea what you are trying to accomplish, but Ubuntu itself did nothing harmful to your computer. What are you trying to accomplish?

---

### Post by Throbbing Gristle on 2010-01-07
Basically fooling around trying to get my Alfa AWUSO5ONH usb to work with the Mad Wifi patch. It started working with the 904 Ubuntu Jaunty. However at the time I had the laptops built in wifi turned on when it search for drivers so the wifi Alfa ran unstable. I have absolutely no Idea how to patch it as I am new to linux. I would like to have my laptop running with Kubuntu 904 as I liked the screen shots of it. My problem is no support for intel graphics mostly at the moment. 

I got further distracted with Ubuntu studio 804 thought I give that a shot then upgrade it to a Kubuntu 904.   Same thing gets stuck at boot up. This pig works flawless with Ubuntu 810 and 804 with no Alfa usb . Thats a lot of distractions for me!

---

### Post by Throbbing Gristle on 2010-01-07
UbuntuStudio 804 was a problem to never could get it to boot........ Later tonight starting back with the Ubuntu 804. It allways worked on that one. Looking deeper on studio I saw it did not have phigh-xservere.org could not be found or installed? Oh I have been reading every where on google![COLOR=#990000]
[/COLOR]

---

### Post by Throbbing Gristle on 2010-01-08
Had to go back to Ubuntu 804 just to bring the computor back to life. Have upgraded to 810 working my way up to 904 now by doing the distro upgrades. Has any one in my pickle ever got the 910 to work I sure did like the Kubuntu it looked nice?

---

### Post by Throbbing Gristle on 2010-01-08
**Boot failures on systems with Intel D945 motherboards**

  Users have reported slower than normal detection of SATA hard drives on systems with Intel D945 motherboards in Ubuntu 9.04. This may cause the system to drop to a busybox initramfs shell on boot with a "Gave up waiting for root device." error. Wait a minute or two and then exit the initramfs shell by typing 'exit'. Booting should proceed normally. If it doesn't, wait a bit longer and try again. Once the system boots, edit /boot/grub/menu.lst and add rootdelay=90 to the kernel stanza for your current kernel. ([290153]("https://bugs.launchpad.net/bugs/290153")) 
[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)


I am in the kubuntu 904 desk top now how do I edit the grub menu this is not clear to me. Can this be done before boot up? Say in 910 versions of Ubuntu? I am back where I started my Alfa usb wirless is running stable now. Takes 20 minutes to boot up though.

904 Ubuntu install tutorial Intel Mother boards on google or here says no matches
Found this but don't know what to do with it or think of it any input?

Add rootdelay=90 to the kernel stanza for your current kernel I have no idea!

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/")

---

### Post by Throbbing Gristle on 2010-01-08
I would love to try Ubuntu studio if I can fix my pressing problem...
[http://ubuntuforums.org/showthread.php?t=448386](http://ubuntuforums.org/showthread.php?t=448386)

---

### Post by Throbbing Gristle on 2010-01-08
Well so some other poor soul such as myself should not have to suffer when a googling. I found the answer to the issue of....
Users have reported slower than normal detection of SATA hard drives on systems with Intel D945 motherboards in Ubuntu 9.04. This may cause the system to drop to a busybox initramfs shell on boot with a "Gave up waiting for root device." error. Wait a minute or two and then exit the initramfs shell by typing 'exit'. Booting should proceed normally. If it doesn't, wait a bit longer and try again. Once the system boots, edit /boot/grub/menu.lst and add rootdelay=90 to the kernel stanza for your current kernel. (290153) 
 [http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)


As I was nut aware of how to go about it. In this link someone was cool about it and showed how!!!!
[http://ubuntuforums.org/showthread.php?t=1137272&highlight=rootdelay=90](http://ubuntuforums.org/showthread.php?t=1137272&highlight=rootdelay=90)


regarding the startup issue "Gave up waiting for root device" that leaves the user at initramfs prompt
 
   He was able to fix this problem by editing /boot/grub/menu.lst (edit the file by opening a terminal and typing sudo gedit /boot/grub/menu.lst) Scroll down to the bottom of the file.
 
 Initially my menu.lst looked like this:
 
Code:
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        254139e0-a67c-4d72-b7c1-442b616f6dc9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=254139e0-a67c-4d72-b7c1-442b616f6dc9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

 I added rootdelay=90 before the word splash, so it looks like this:
 
Code:
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        254139e0-a67c-4d72-b7c1-442b616f6dc9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=254139e0-a67c-4d72-b7c1-442b616f6dc9 ro quiet rootdelay=90 splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet


Really helped me!!

---

### Post by Throbbing Gristle on 2010-01-08
Looking at the letters 1st lst was where I messed up. Go figure? I still have to boot up in the latest kernel with 904 to get the Alfa usb wifi to work at all. Which means having to tap the Esc button then enter on the key board any way of correcting that?

---

### Post by Throbbing Gristle on 2010-01-13
Ran into another good read!! I will keep posting here on this subject so someone can get there easier than I did! This one concerns installing a 9.10 Ubuntu distro and that dreaded Intel blank screen dilemma..:popcorn:

[http://maketecheasier.com/solving-ubuntu-karmic-black-screen-issue/2009/12/29](http://maketecheasier.com/solving-ubuntu-karmic-black-screen-issue/2009/12/29)

---

