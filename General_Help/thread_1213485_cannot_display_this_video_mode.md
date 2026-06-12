---
title: "cannot display this video mode"
date: 2009-07-14
forum: General Help
---

### Post by hotshot247 on 2009-07-14
when i try to boot into ubuntu 9.04 (it did the same thing with 8.10), right before it hits the GUI, it says "cannot display this video mode" and nobody seems to know how to fix it. somebody told me that i need to edit the xorg.conf file but they could never tell me what to type in. another person told me that it had something to do with my nvidia card and that i needed to edit the xorg.conf file to fix it but nobody seems to be able to tell me what to type in the file. any help would be appreciated. thanks in advance!!

---

### Post by overdrank on 2009-07-14
> **hotshot247 said:**
> when i try to boot into ubuntu 9.04 (it did the same thing with 8.10), right before it hits the GUI, it says "cannot display this video mode" and nobody seems to know how to fix it. somebody told me that i need to edit the xorg.conf file but they could never tell me what to type in. another person told me that it had something to do with my nvidia card and that i needed to edit the xorg.conf file to fix it but nobody seems to be able to tell me what to type in the file. any help would be appreciated. thanks in advance!!

Hi and welcome, what is the model of the nvidia graphics card?
Have you checked the cd for errors also?

---

### Post by hotshot247 on 2009-07-15
it's a NVIDIA Geforce 6800 and also, i made my usb flash drive bootable with a program called UNetBootin and i installed ubuntu with the flash drive. i've also tried with a cd and it did the same thing. i've even tried to upgrade from 8.10 to 9.04 because i thought it might have been a bug that they fixed or something. usually i can figure stuff like this out. lol thanks for your help

---

### Post by hotshot247 on 2009-07-15
i figured it out and i wrote a small tutorial on how to fix it for anybody who needs it. i have a NVIDIA 6800 but i'm sure it'll work on all NVIDIA's. 

  	 	 	 	 	 	  How to get a NVIDIA Geforce 6800 card to work with ubuntu linux
 

 When you boot up into ubuntu right before it gets into the gui, it will say “cannot display this video mode”.
 

 
[LIST=1]
[*]Press “Ctrl + Alt + F1 and it 	will take you to a prompt
[*]Edit the xorg.conf file by typing 	“sudo nano /etc/X11/xorg.conf
[*]Add the lines that are missing in 	this file:
[/LIST]
 		Section “Monitor”
         			Identifier	“Monitor 1”
         			HorizSync	30.0 – 80.0
         			VertRefresh	56.0 – 76.0
         			Option		“DPMS”
 		EndSection
 

 

 		Section “Screen”
         			Identifier	“Screen 1”
         			Device		“<Device>”
         			Monitor	“Monitor 1”
         			DefaultDepth	24
         			SubSection	“Display”
                     				Display	16
                     				Modes		“1280x1024”
         			EndSubSection
          SubSection	“Display”
                     				Display	24
                     				Modes		“1280x1024”
         			EndSubSection
          SubSection	“Display”
                     				Display	32
                     				Modes		“1280x1024”
         			EndSubSection
 		EndSection
 

 
[LIST=1]
[LIST=1]
[LIST=1]
[*]When you try to boot into ubuntu 			now, it will say “Ubuntu is running in Low graphics mode” blah 			blah blah. Just exit out of that and it'll have an option, I forgot 			what it says but just hit yes and it will boot you into ubuntu.  			
[*]Now you're in ubuntu gui now but 			the video display is still not displaying right.
[*]Click system at the top then 			administration then “NVIDIA X Server Settings and it will tell 			you that the video card is not properly configured and it will 			tell you something to type into the terminal.
[*]Open the terminal and type 			“sudo” and then whatever NVIDIA told you to type in and it 			writes a new config file.  			
[*]Restart computer and it should 			work.  			
[/LIST]
[/LIST]
[/LIST]

if you have any questions, let me know.

---

