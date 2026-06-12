---
title: "I finally upgraded to 12.04 from 10.10. Now I cant boot to windows xp!"
date: 2012-06-18
forum: General Help
---

### Post by amaruq_atka on 2012-06-18
I finally upgraded to 12.04. I dont like it, I dont want it. I want it gone. Before I upgraded, all I had to do was unplug the external I have it on, or just tell my computer BIOS to boot from the internal drive. Grub messed that all up. Now when I try to boot to windows it tells me "no such device" and then gives me a grub rescue prompt. I want to remove grub, and go back to windows. I know I can use windows instalation to restore the MRB, but like 99% of people out there, I dont have the disks, it came pre-installed. This means I cant access it at all. How do I get rid of grub, or atleast to be able to access my windows drive again?

---

### Post by sudodus on 2012-06-18
You will find an excellent guide in the following link
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1195275_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")
Please ask if you need more help.

(And I hope that you manage to get the dual boot system working nicely again.)

---

### Post by wilee-nilee on 2012-06-18
Use the boot-repair tool from a ubuntu install or a live ubuntu cd to generate the bootinfo summary, and post the HTTP address to it.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

This script will give a outline of your set up.

There is a linux boot manager that will boot windows without ever seeing the manager as well.

It is shown in the link in the post above, above as lilo

---

### Post by amaruq_atka on 2012-06-18
None of these work. But I have identified the problem. I only get that error when the drive with ubuntu isnt plugged in. It is an external. Only if there was some way to get grub onto the interal drive with windows. boot repair acts like I can do that, it has a drop down, but it is just a placebo button and no list comes.

---

### Post by wilee-nilee on 2012-06-18
> **amaruq_atka said:**
> None of these work. But I have identified the problem. I only get that error when the drive with ubuntu isnt plugged in. It is an external. Only if there was some way to get grub onto the interal drive with windows. boot repair acts like I can do that, it has a drop down, but it is just a placebo button and no list comes.

If you just have windows on the internal, you would not use grub. 

Although you can use lilo to boot windows from that internal.

Care of another users instructions, also in the first link post 2.

                                  [FONT=Verdana, sans-serif][SIZE=1]Restore basic windows boot loader - universe enabled [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]open synaptic-settings-repositories, first tab, tick universe, close those windows and open a terminal, and run these commands [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]sudo apt-get update [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]sudo fdisk -l   (confirms hd=sdX, and windows partitions) [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]sudo apt-get install lilo [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]sudo lilo -M /dev/sda mbr [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]May show error messages about the rest of lilo missing, ignore, we just want MBR [/SIZE][/FONT]

---

### Post by amaruq_atka on 2012-06-18
Thanks to everyone, I finally got it. I found the solution at

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)


I used lilo to re-do the MBR on the internal and its working fine.

---

### Post by sudodus on 2012-06-18
I was just writing a long help text, but it's not necessary now. Glad you solved the problem :-)

Please click on **Thread Tools** at the top of this page and mark this thread as SOLVED

---

