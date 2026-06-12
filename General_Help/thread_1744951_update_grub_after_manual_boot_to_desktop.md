---
title: "update grub after manual boot to desktop"
date: 2011-04-30
forum: General Help
---

### Post by joe carolan on 2011-04-30
Updated to natty had problems (boy what a lot of whiners on the forum) I have spent a lot of time searching Google to sort out most of my problems but need help with updating grub.
After installing natty i got a frequency out of range error on boot up and nothing else.
Anyway i can now boot to my desktop after using live CD to recover  and natty loads with unity desktop. (unity looks good to me) after booting from grub prompt into desktop however, although i have done  a sudo update-grub from the terminal and apt-get upgrade, when i shutdown i do not get the boot menu on restart  (i  go back to grub prompt)
System is duel boot win7 Ubuntu how can i fix grub permanently and get back boot menu. 
any help greatly appreciated
joe

---

### Post by oldfred on 2011-04-30
Welcome to the forums.

You need to reinstall grub2's boot loader to the MBR. If you can manually boot it should just be :

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sda"  then just run:
[COLOR=DarkRed]sudo grub-install /dev/sda[/COLOR]
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

If you cannot boot then the liveCd has to mount the install partition (/boot if separate partition).
#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5 (if separate /boot also mount it)
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by joe carolan on 2011-04-30
to Old Fred
Thanks a million all fixed up 
I am quiet new to forum and not sure how to mark this thread as solved but when i figure it out i will mark it as solved
Thanks again 
joe

---

