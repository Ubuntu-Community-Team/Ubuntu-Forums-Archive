---
title: "Grub Error 15 after 11.04 Natty Narwal installation"
date: 2011-06-06
forum: General Help
---

### Post by professorbell on 2011-06-06
Story:

Installed 11.04 Natty Narwal from a live cd on my 2 year old HP Elitebook. 

The installation completed successfully according to the Live Session.

I restart...

> GRUB Loading stage1.5

GRUB loading, please wait...
Error 15



I have 2 other operating systems on the hdd, that I was previously managing with grub which was stored in the boot directory of Ubuntu 9.04 (on the partition that I formatted to install 11.04)



What I have on hand:

A live CD (from the install) a second laptop

No experience with Grub2

Some degree of frustration at the error: 

> cannot stat 'aufs'.

which is thrown whenever I try to run update-grub2 or any other grub related command from the live CD


Any help/advice would be greatly appreciated. 

(Though an explicit walk-through with quoted commands is more specifically what i'm looking for.)

---

### Post by oldfred on 2011-06-06
Error 15 is usually conflicts with grub legacy & grub2.

Standard reinstall of grub2's boot loader to the MBR. With 11.04 be sure to use Natty liveCD as 1.99 seems to have enough changes that others do not work.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

You cannot run sudo update-grub from a liveCD. You do run it anytime you edit grub's config files or it will run in the background for grub2 or kernel changes.

---

### Post by professorbell on 2011-06-06
Problem solved.

Thank you very much for the assistance.

---

