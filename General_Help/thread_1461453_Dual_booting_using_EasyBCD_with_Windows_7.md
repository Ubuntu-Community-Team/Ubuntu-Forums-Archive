---
title: "Dual booting using EasyBCD with Windows 7"
date: 2010-04-24
forum: General Help
---

### Post by fterh on 2010-04-24
Hello,

I'm using the latest version of EasyBCD (as of now) to dual boot Ubuntu with Windows 7. I added an entry "Ubuntu 10.04" to the boot menu, selecting Grub as the type.

However when I choose Ubuntu upon startup I get this.

[IMG]http://i40.tinypic.com/nprlac.jpg[/IMG]

Upon hitting any key I get this.

[IMG]http://i41.tinypic.com/35d163k.jpg[/IMG]

Wanted to mess around with Grub and mbr, but I'm afraid I'll screw my hard drives up. Decided to post here for help instead :)

---

### Post by klemes on 2010-04-24
I ve used easyBCD with Vista.The only option allowing me to boot into Ubuntu was using the super-grub option and let it add an entry automatically for a Linux partition
Wish I could help you a lot but it's been a long time that I don't use this particular setup anymore and don't remember any more details.

---

### Post by fterh on 2010-04-25
> **klemes said:**
> I ve used easyBCD with Vista.The only option allowing me to boot into Ubuntu was using the super-grub option and let it add an entry automatically for a Linux partition
Wish I could help you a lot but it's been a long time that I don't use this particular setup anymore and don't remember any more details.

Never mind got it. Had to set my BIOS boot sequence because Ubuntu (and Grub) is on a different hard drive than Windows 7 :D

---

### Post by asvraman on 2010-10-06
I have a similar problem help please

I bought four days ago a DELL Inspiron N4010 with pre installed windows 7. I cretaed a partition and installed Ubuntu. So far fine. I was able to use ubuntu and windows 7 any number of times.

I used EasyBcd to alter the boot sequence by adding an entry for ubuntu and writing the entry in MBR. Used grub legacy. I now read that I should have used Grub 2. The mbr was written in the recovery (2) partiton of Dell. Windows 7 is in 3rd partiton(c).

Now once I enter windows and come out I am not able to reboot.

I can do grub install from Live CD of Ubuntu and enter windows again but once I shut down it does not reboot.

Help please

asvraman 

[IMG]file:///C:/Users/asv/AppData/Local/Temp/moz-screenshot-1.png[/IMG][IMG]file:///C:/Users/asv/AppData/Local/Temp/moz-screenshot-2.png[/IMG]

---

### Post by oldfred on 2010-10-06
Most of us here use grub or grub2. You may do better at the neosmart site with easyBCD errors.

[http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home](http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home)

Why not easyBCD - Herman's post
[http://ubuntuforums.org/showthread.php?t=1554155](http://ubuntuforums.org/showthread.php?t=1554155)

---

