---
title: "Ubuntu and Windows 7 Setup Dual Boot"
date: 2010-11-19
forum: General Help
---

### Post by Sunrock on 2010-11-19
I have been hearing good things about Linux and Ubuntu so I decided to try Ubuntu.   If all goes well, I will switch from Windows to Ubuntu.  Recently, I purchased a second HDD to install the most recent version of Ubuntu. On my primary HDD I have Windows 7 installed.  Prior to installing Ubuntu I did some online research to determine how to select which OS I want to boot.  I set the BIOS so the HDD with Ubuntu (second HDD) boots first to pick up the Ubuntu GRUB menu.  Then, I can select which OS will boot.  The articles mentioned that I can control this with the file “/boot/grub/menu.lst” but I was unable to locate this file.  Later, I found out that Ubuntu or the Linux community did away with this in favor of “Grub 2.”  Anyway, I found the file “/etc/default/grub” which is supposed to update the file “/boot/grub/grub.cfg.”  I am trying to supply enough information so someone can help me solve the following problem.  When I reboot, I hold down the <Shift> key and the following menu pops up.

GNU GRUB version 1.98+20100804-5ubuntu3

Ubuntu, with Linux 2.6.35-22-generic-pae
Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)
Memory test (mentest86+)
Memory test (mentest86+, serial console 115200)
Windows 7 (loader) (on /dev/sdb1) 


When I first see this menu the second line “Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)” is highlighted so if I do not make a selection within 10 seconds the PC boots into the recovery mode.   For now, I want the PC to automatically boot to “Windows 7 (loader) (on /dev/sdb1)” if I do not make a selection but I have not been able to figure out how to set this Windows 7 default boot.  I have tried editing the file “/etc/default/grub” but to no avail.  If this is the correct file to edit, would someone please give me an example of how this file should look like.  

Thanks!
Sunrock

---

### Post by wilee-nilee on 2010-11-19
n

---

### Post by ksprasad on 2010-11-19
Hi Sunrock,
 
“/etc/default/grub" is the correct file you are editing.
 
Just set "GRUB_DEFAULT=4" since entry starts with 0.
 
Also dont forget to run "sudo update-grub"
 
Regards,
ksprasad

---

### Post by oldfred on 2010-11-19
ksprasad way is good and I recommend understanding grub2, but some prefer GUI.

Startup manager (SUM) in synaptic will allow you to set boot default and the timeout even with grub2.
the quick and easy to make a default boot:

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

More info on grub2:
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Sunrock on 2010-11-20
I tried Ksprasad's suggestion and it worked great.  I edited the file "/etc/default/grub" and changed "GRUB_DEFAULT=1" to "GRUB_DEFAULT=4." Then, I ran "sudo update-grub." I rebooted and it automatically booted to Win 7.  Later I will look at Oldfred's suggestion so I can learn more about Linux.  Thanks for all who responded.  I did not expect such a quick response so this was nice.  Thanks!

---

