---
title: "boot menu does not show ubuntu as an option"
date: 2010-08-24
forum: General Help
---

### Post by spt025 on 2010-08-24
hey guys i reintalled my xp formatting its both drive ...

I had ubuntu 10.04 installed seperately on hard disk. But now boot menu doesn't show the option of ubuntu 10.04...

It just starts the windows xp .

ubuntu is still installed i know that for sure ...
but don't know how to access it ..
....
I am at beginner level ....
thank you all in advance for reply

---

### Post by borth92 on 2010-08-24
did you install xp after Ubuntu?

---

### Post by spt025 on 2010-08-24
yes i installed xp after ubuntu

---

### Post by spt025 on 2010-08-24
ya but at the time of installation of xp i didn't format drives which had ubuntu 10.04

---

### Post by borth92 on 2010-08-24
Windows OS's automatically delete the GRUB boot loader and installs the windows one. The windows boot loader does not recognize linux operating systems so it just goes right into the "only" OS, which in your case is xp. Boot into a Ubuntu live CD, and reinstall GRUB. Ill look for a link to aid you in the reinstallation of GRUB.

---

### Post by borth92 on 2010-08-24
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

The GRUB loader will show ubuntu and windows

---

### Post by dtoronto on 2010-08-24
sounds like you xp set to override the grub, you may need to set your bios settings in your machine to boot to the HDD with your ubuntu installation and then run the update-grub again after you get into ubuntu

---

### Post by spt025 on 2010-08-24
how to reinstall GRUB boot loader ????

Do provide the link if you find because i know nothing about it

---

### Post by spt025 on 2010-08-24
TO [dtoronto]("http://ubuntuforums.org/member.php?u=732535")
How to do so ..
i know how to go in to bios ..
but after part i didn't understand ...
bit detail would be much of help

---

### Post by borth92 on 2010-08-24
link is right below my first explanation

---

### Post by borth92 on 2010-08-24
it is not in the bios, you need to install grub. windows deletes it...ive had this problem when i was new to linux

---

### Post by spt025 on 2010-08-24
ohh i am sorry this is my first post so in excitement i made a mistake ...
Thnk you "borth 92" & "_dtoronto_" for help

---

### Post by spt025 on 2010-08-24
thnx guys .....
thank you both

---

### Post by spt025 on 2010-08-25
[http://ubuntuforums.org/search.php?searchid=75494333](http://ubuntuforums.org/search.php?searchid=75494333)

hey guys i tried this link & the other link provided in this thread  earlier also but yet my probe is unsolved /....
grub is not being installed ....
when i write 

sudo chroot /mnt/root /bin/bash

it shows me error that "chroot: cannot run command `/bin/bash': No such  file or directory"
plus when i write 

find /boot/grub/stage1

it shows error no. 15.....


please help me

---

