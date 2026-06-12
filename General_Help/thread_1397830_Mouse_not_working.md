---
title: "Mouse not working"
date: 2010-02-03
forum: General Help
---

### Post by forestwalker101 on 2010-02-03
So heres my problem.  I recently installed unbuntu 9.1 on my desktop that i built a few years back and I really like it but ive been getting really frustrated over the fact that my usb mouse stops working anywhere from 30 seconds to 30 minutes of use. I tried using this: 
 	Quote:
 	 	 		 			 				 					Originally Posted by **lisati** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=5353658#post5353658") 				
 				[I]One topic that crops up from time to time in these forums is what to do if devices connected by USB stop working when the computer has been turned on for a while, but come right when the computer is rebooted.

The following solotuion is what I used when my USB mouse and USB keyboard worked fine at startup but stopped working after a while. I have successfully used it on a Toshiba A100 laptop running Ubuntu 7.04, a.k.a. "Feisty".
[I][B]
Disclaimer:[/B] The success (or otherwise) of the following solution will depend on your hardware and possibly which version of *buntu you are using. Feel free to add your feedback to this thread and alternative solutions
[/I]


[LIST=1]
[*]From a terminal, type  	Code:
 	gksudo gedit /boot/grub/menu.lst 
 You will be asked for your password - don't worry if your password doesn't show, this is normal. Just type in your password as usual, and it will be accepted.
[*]When the editor opens, scroll down to the line which reads  and change it to read  	Code:
 	# defoptions=quiet splash acpi=force irqpoll 
[*]Save the file, exit the editor
[*]From the terminal, type in  	Code:
 	sudo update-grub 
[*]Restart your computer.
[/LIST]
[/I]
 			 		 	 	 
But after i enter my password i just get a blank window. Ive tried three different usb mice in two different usb ports and they all do the same thing.  Im currently using a P5NSli motherboard and a 1.8ghz C2D.  Any help would be greatly appreciated.

---

