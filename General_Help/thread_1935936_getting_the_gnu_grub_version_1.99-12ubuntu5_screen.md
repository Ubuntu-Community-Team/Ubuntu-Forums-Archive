---
title: "getting the gnu grub version 1.99-12ubuntu5 screen for nothing"
date: 2012-03-05
forum: General Help
---

### Post by reychun on 2012-03-05
Ubuntu has always been working fine, I was just switching on my computer as usual and suddenly the screen for gnu grub version 1.99-12ubuntu5 appears even though I am not installing ubuntu.

the following options provided:
Ubuntu, with linux 3.0.0-1-generic
Ubuntu, with linux 3.0.0-1-generic (recovery mode)
Previous Linux versions
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

they are asking me to select which OS I would like to boot but I am so confused. Please tell me what to do to escape and still protect my files (in my computer) from being deleted.:confused:

---

### Post by raja.genupula on 2012-03-05
when you're getting that , at boot time or some thing else?

when you get menu like this are you getting anything time at bottom of screen like 10 sec or something .?

---

### Post by reychun on 2012-03-05
okay i got the problem solved by just taking the risk of selecting the first option. but i still don't understand why I got that gnu grub screen. The computer was just setting up normally. The gnu grub stayed forever. :(

---

### Post by raja.genupula on 2012-03-05
Its just a grub screen my friend , if your system having only Ubuntu then grub menu wont appear and directly boost into Ubuntu  but if you have dual system it will appear , to get rid of that only i have asked you that are you seeing anything like time at bottom of screen ? 

cheers! 

Raja

---

### Post by indianrainbow on 2012-04-20
Hi Raja,

I have exactly the same screen when I boot up. I do not have a timer at the bottom of my screen counting down. Nothing works on my keyboard. I can't get it to do anything. I have very little knowledge about computers. My screen went blank and took it to a tech. He had it for two months and couldn't fix it. Finally got it back and thought I would try myself. Read up about the unplug, tale battery out, hold for 30-60 sec , plug in, boot up and then put battery back in theory. It worked....I got so excited .... only to end up with the above screen as mentioned. I have a HP pavilion entertainment laptop. Can you please help?????

---

### Post by grahammechanical on 2012-04-20
To add a little bit more to what Raja said, When Ubuntu installs it also puts a boot loader in a certain part of the hard disk called the Master Boot Record (MBR). This happens every time that we install Ubuntu. If there is a second operating system on the machine then this Grub menu can be used to boot into either operating system.

If there is only Ubuntu on the machine then we do not usually see this menu but it is there nontheless and will automatically boot the Linux kernel that is at the top of the list. Ubuntu is built on Linux remember? So, we see Linux not Ubuntu.

The timer does not count down but there usually is a message saying that we have ten seconds to select a kernel both the default will boot.

@indianrainbow

can you write down everything that you see on the screen when you get this 
menu? And then post it here. This would help us to confirm what your situation really is.

Regards.

---

### Post by indianrainbow on 2012-04-20
Hi Graham, 

Thank you for your reply and explanation. Very much appreciated. I have copied exactly what i see on my screen as requested. 

GNU GRUB  version 1.99-12ubuntu5

Ubuntu, with Linux 3.0.0-17-generic
Ubuntu, with Linux 3.0.0-17- generic (recovery mode)
Previous Linux versions
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

Use the up arrow and down arrow to select which entry is highlighted. Press enter to boot the selected OS,  'e'  to edit the commands before booting or 'c' for a command line.

Could not find the symbol for the up and down arrow as shown on screen.

---

### Post by daemoncycler on 2012-12-01
Hi
Yesterday I started to get the same msg & don't know why?

Lubuntu 11.10 only - no other OS.  Removed Windows 6 months ago in favor of Lubuntu.

My machine does boot automatically after 10 seconds.
Did not to my knowledge shut the PC down during any kind of install.


Been researching this most of the morning (noob here) & performed a couple actions that may not have been necessary but were interesting nonetheless.

1) think I have successfully run the boot-repair from downloaded .iso.  Had to run it in failsafe mode, non failsafe mode just hung each time I tried it.  It did indicate one problem fixed & that the document would be avail to view after restart.  However after restart from HD I cannot find the document that Boot-Repair generated.  Don't remember exactly what it repaired :(


2) ran from terminal (booted from Lubuntu install CD into "try Lubuntu before installing")```
fsck -a /dev/sda1
```  found no errors.


Ran another command found on the Ubuntu forum:
```
sudo shutdown -r -F now
```
also found no errors.


Neither Boot-Repair nor fsck cleared the startup msg = GNU GRUB version 1.99-12ubuntu5.1


Why did this msg start to appear all of a sudden?
Have I done something to the MBR?
Should I start a new thread?

thanks

---

