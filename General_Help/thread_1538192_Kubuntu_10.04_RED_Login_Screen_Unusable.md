---
title: "Kubuntu 10.04 RED Login Screen Unusable"
date: 2010-07-24
forum: General Help
---

### Post by AsgerJorn on 2010-07-24
Hi

I have just installed Kubuntu 10.04 i386 on a Dell Vostro 1500 ('08), with an "alternate" installation ISO file.
When I boot and select the correct partition the login screen is red and two red lines appears across the screen. One can see a light-animation, but the image is doubled and it is impossible to see or do anything.
I have tried booting in recovery mode, it didn't solve anything.
This problem also occured when I tried booting Kubuntu from CD.

Have anyone tried this before, or have a solution?

Thank you very much.

---

### Post by robsoles on 2010-07-24
Please tell me which of the (apparently) two graphics controllers that laptop is using - there is an Ok chance of installing it via the terminal.

Next time you are looking at the red blotchy display please press [CTRL]+[ALT]+[F4] and confirm for me that you can read the display in the terminal login prompt that (hopefully) appears on your display - we are going to need this to get your graphics drivers working.

---

### Post by AsgerJorn on 2010-07-25
Hi I tried following your instructions, but nothing happens when I press Ctrl+Alt+F4, atleast nothing I can see on the screen.

How do I find out wich of the two graphics controllers the laptop is using?
I'm a bit inexperienced, so could you explain what you mean by graphics controller? - just to avoid a misunderstanding.

Thank you for your help.
I appreciate it.

---

### Post by robsoles on 2010-07-25
"Graphics Controller" is other words for "Video Card" or perhaps even "VGA Device".

[http://www.linlap.com/wiki/dell+vostro+1500](http://www.linlap.com/wiki/dell+vostro+1500) says that there are two different nvidia graphics controllers that your laptop came out with so pursuing the problem will be assisted by knowing which one it is for sure.

It may be written somewhere on the case of the laptop, post back if you just can't find it and I will do more digging in Google for something that will (hopefully) just tell you so you can post it here.

The fact that that page I linked to says the video is compatible may mean that your video controller is broken but lets ignore that and try to make it work by making it use the right drivers first.

That will be a major pain in the neck if you don't get to see a terminal login prompt when you press [CTRL]+[ALT]+[F4] when you are looking at the scrambled GUI login screen - much harder to force in the manufacturer drivers if we can't even see in terminal!

---

### Post by AsgerJorn on 2010-07-26
Oh that's what I thought :). 
Video card info:
Nvidia GeForce 8600M GT 512mb ram

I am using the laptop with my WinXP partition (kept it for safety reasons ;)) so the hardware should work. Ubuntu worked aswell, only Kubuntu has caused this problem.
What if I try installing and older version of Kubuntu?

Edit: I really appreciate your help, because I was on the tip of calling the Canonical phone support. So thank you.

---

### Post by robsoles on 2010-07-26
Have a quick look at previous version of Kubuntu off a LiveCD but I fear it will fall down the same.

If Ubuntu worked on the Laptop perhaps the people managing Kubuntu don't even try to support that video card - just an idea.

I assume you don't keep Ubuntu and try Kubuntu because Ubuntu is a little slow on the Laptop - did you try the 'laptop remix' of Ubuntu? Perhaps Lubuntu supports that video card straight up.

We will need to access the terminal SH/BASH to install the manufacturer's driver for your GeForce 8600 - If you press shift while the LiveCD of Kubuntu is booting do you get a readable menu of choices? If you do then can you pursue one of them to get Kubuntu installed to your empty partition?

When you boot Kubuntu it should be possible to get a terminal but maybe not off the LiveCD - to be honest I didn't try Kubuntu yet but I can't see why they wouldn't support [Ctrl]+[Alt]+[F4] method to access a terminal.

---

### Post by AsgerJorn on 2010-08-14
The menu for installation is fully available and usable with both the LiveCD and the AlternateCD. But when I start Kubuntu from either cd or installation, what I can only guess is, the login screen is completely useless graphically - no terminal (or anything else) to see what so ever, except some fading colors of red and white changing when I press the arrow keys.
I'll try the Netbook CD. :)

---

### Post by AsgerJorn on 2010-08-16
I have now tried the Netbook CD and that didn't work either.
Now I am sort of lost, to be honest.

---

### Post by AsgerJorn on 2010-08-16
I found this thread: [http://ubuntuforums.org/showthread.php?p=9726660#post9726660](http://ubuntuforums.org/showthread.php?p=9726660#post9726660)
Seems to have to do with the same problem - same specs.

This picture illustrates the exact problem I have:
[http://photo.lujun.info/main.php?g2_itemId=5554&g2_imageViewsIndex=1](http://photo.lujun.info/main.php?g2_itemId=5554&g2_imageViewsIndex=1)


From the thread linked above:

"I was able to get this working in a two pronged approach:
 
On the initial install, you need to hit F6 and select nomodeset as the extra option (on the boot-up menu where you first select your language and then select the "install ubuntu" option, you are adding this option before you hit enter, from the F6 menu). This will allow you to boot into the GUI. 

Once the install is done, it will reboot with the same problem. From here, what you need to do is select the recovery option inside of grub and edit the line that has all the options (ro quiet splash etc). You need to place the nomodeset option in amongst those other options (keep seperated by a space) and boot up (once you add the nomodeset parameter, hit ctrl-x to boot that kernel with your parmaters). Once the system gets to the recovery menu (which you can read now) tell it that you want to drop to a shell with network.

Once you are on a shell with network, it seems as though a simple "sudo apt-get update; sudo apt-get upgrade" does the trick, although to be sure I just installed the nvidia binary driver "sudo apt-get install nvidia-current".

This was the only combination of tries that was successful for me, after a bunch of attempts. Hopefully this is a help to other Vostro 1500 or Nvidia 8600M users who were struggling to get an initial install.:razz:

Edit: The technical problem is the nuveau driver that is now used.. it sets the modeline incorrectly, and by default. There are other kernel-flag workarounds to disable this modeline setting but this is the seemingly best way to do it with only the vanilla installer disk. FWIW this was all done on an i386 copy as the Vostro is capped on RAM and 64b doesn't matter for me on the portable.
 		                   		  		  		  		  		 		 			 				 				* 					 						Last edited by theduke88; July 2nd, 2010 at 01:55 PM.. 					 					 						Reason: Adding some info*"


I'm lost at section two of his post. Perhaps you can explain it better?

---

