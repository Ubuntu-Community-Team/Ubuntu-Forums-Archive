---
title: "Can not Boot - Can not find C/H/S Grub Issue? Bug?"
date: 2010-01-24
forum: General Help
---

### Post by newtounbuntu on 2010-01-24
[COLOR=black][FONT=Verdana]I am posting this in the hope of assisting someone. I have resolved by issue and am reporting how.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I took my old Dell out of the closet and restored it to life. I wanted to build a media server. My system is as follows.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Old Dell 4600 with Bios A7[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Intel 1.6GHz P-IV[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]2.5 Gigs of Memory[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Two WD 1T SATA disks in RAID 1 configuration.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Two IDE cd drives[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]No IDE hard Drives[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]No Floppy[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]800 MHz motherboard[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Installed Ubuntu 9.1 Server and installed the Ubuntu Desktop.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]After struggling with RAID I finally tried to boot. The machine would not boot and ended up in grug rescue mode. It gave me the following error. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Can not get C/H/S and then would send me to the grub rescue prompt.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]From the prompt, if I typed[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]insmod normal[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]pressed enter, and then typed[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]normal[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]The machine would complete booting and enter the operating system.[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Verdana]I worked for a week or so with the booting problem, could not find a solution and I just got used to typing [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]insmod normal[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]normal[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]It bothered me so I kept searching. Today I found the following.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=564083](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=564083)[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Apparently the C/H/S values are getting across from bios but there is a problem.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I don't have a floppy on this machine and had the Bios set accordingly. I experimented with the bios and set the bios as if I had a floppy. I tried to reboot and it booted without any additional command. The machine now boots without any intervention.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Apparently on this Dell 4600 Intel motherboard if you shut off the floppy drive in bios you will get the, can't get C/H/S error, and will be thrown into grub rescue. IF you fake the machine to think it has a floppy it will boot without intervention.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Thought this might help someone else.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]By the way I can't get Mediatomb to be detected by anything on my network; PS3 and two window's vista machines. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Oh well that is for another post.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Would appreciate hearing back from someone who was helped by this post.[/FONT][/COLOR]

---

### Post by MurphS on 2010-04-20
Hi,
 I too have an older Dell and am having the very same problem. I don't know if your post has helped or not, yet, but I certainly expect that it will!:) 

Thanks, Scott

---

### Post by rgabo on 2010-04-27
I took the time to register to thank you. After a half day of troubleshooting, I came in this morning and found your post. After confirming that 'insmod normal; normal' worked flawlessly, I re-enabled the floppy drive in our Dell PowerEdge SC440 and GRUB2 boots perfectly.

You are my personal hero today.

**Thanks!**

---

