---
title: "NVIDIA video SUPER bad graphics during games."
date: 2010-06-18
forum: General Help
---

### Post by pussaybanger on 2010-06-18
What is causing this graphic distortion?

I dropped Vista because this problem would crash the video driver and pop a black screen for a few seconds over and over and over and over.

Now that I installed ****ING Ubuntu it's doing this problem, but without the black screens and only messed up graphics show.

So what the heck guys, is this a hardware or software problem? And this same type of graphic distortion appears in games like Combat Arms and Halo.


I am so SICK of NVIDIA never ever in my whole entire life will I ever buy NVIDIA again! Luckily for nvidia I'm only 17 years old and have 40 years of life left to buy computers without nvidia in them. Until I save up dough for a new computer "without nvidia" I'll keep trying to fix this. P.S this nvidia chip is tied down to my motherboard.

**These pictures are in Ubuntu 9.10**




[IMG]http://ubuntuforums.org/attachment.php?attachmentid=160801&stc=1&d=1276839233[/IMG]


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=160802&stc=1&d=1276839233[/IMG]




[IMG]http://ubuntuforums.org/attachment.php?attachmentid=160803&stc=1&d=1276839233[/IMG]




[IMG]http://ubuntuforums.org/attachment.php?attachmentid=160804&stc=1&d=1276839233[/IMG]

---

### Post by sandy8925 on 2010-06-18
If it happened in both Vista and Ubuntu then 95% a hardware problem. Could be that the card is heating up a lot or it's just old (my own nvidia card flipped out on me after 3 years of working properly). which card are you using and which driver? (the driver version that is). also make sure the bios settings are correct.

---

### Post by Linuxforall on 2010-06-18
Using language like this will surely get you banned here and with this hind of attitude, good luck in getting help. FYI, nvidia may not be perfect but its competition ATI is a joke, take a look at their drivers for Linux and you will know why. Now you need to post what version of drivers you have installed for nvidia. Also try turning off effects to see if this issue goes away. Black screen during game indicates the GPU going south, I had one 6200 nvidia do that on me a year back.

---

### Post by Spr0k3t on 2010-06-18
If you were having problems with the system while in Vista and experience problems (yet different) while in Ubuntu... there's a very good chance the issue is not software.  I'm guessing you are referring to the verticle lines in each picture and not the output seen in the WINE layer window.  There's a glitch in WINE 1.0-1.1 with the GL translations which causes miscalculations of large level environments.  The latest updates of WINE has fixed the issue.

One thing to try though... install the drivers for the chipset from the repos rather than installing from the binary file from nvidia.  Also, when playing wow, make sure to turn off the extra 3D stuff (compiz/fusion).

---

### Post by pussaybanger on 2010-06-18
[COLOR=Red]"could be that the card is heating up a lot or it's just old"[/COLOR]
This gpu is 2 and a half years old. And it started doing this one day and since that day it has not stopped. It started doing it like 5 months ago. It is the  graphics malfunction of course.

[COLOR=Red]"which card are you using and which driver?"[/COLOR]
Card/chip = GeForce 8400 GS
driver version  = 185.18.36

and I got this driver from the Hardware Drivers utility in the Ubuntu taskbar   System -> Administration -> Hardware Drivers



[IMG]http://ubuntuforums.org/attachment.php?attachmentid=160807&stc=1&d=1276845141[/IMG]



 [COLOR=Red]"also make sure the bios settings are correct."[/COLOR]
how can I do this?



[COLOR=Red]"Also try turning off effects to see if this issue goes away.[/COLOR]"
The effects are now down to the low minimum, and no luck.


 [COLOR=Red]there's a very good chance the issue is not software.[/COLOR]
I had the same graphic distortion in Vista as I do now in Ubuntu, except that Ubuntu doesn't make a black screen pop up.


[COLOR=Red]"you are referring to the verticle lines in each picture "[/COLOR]
Those vertical lines are trouble, but the main problem is the distorted graphics inside the game window (world of warcraft)

[COLOR=Red]"There's a glitch in WINE 1.0-1.1 "[/COLOR]
I've been using Wine 1.2-rc3



[IMG]http://ubuntuforums.org/attachment.php?attachmentid=160808&stc=1&d=1276845141[/IMG]






I don't wanna sound like a suck up, but thanks for your support guys. Really, this thing is making me go insane.

---

### Post by dukhia on 2010-06-18
Have you overclocked your PCIE clock?

Go to the BIOS and "Reset to Defaults" and try again.

---

### Post by sandy8925 on 2010-06-18
To open the bios settings, when the comp is starting up(as in right after you power it on - long before any os starts up) press any of f2,f8,f10,f12 or delete. the actual key varies among different motherboard brands. hopefully the key should be displayed on screen when you start up the comp. going to the bios is only useful if its a desktop. in most laptops the bios does not allow you to change advanced stuff.

if you are using a desktop though, since it's an onboard graphics card you can probably buy a new graphics card and use that.

---

### Post by Linuxforall on 2010-06-18
The driver version is quite old, add the ppa for x by pasting in terminal

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update

Go to update manager and click to update to latest nvidia drivers, not that it would make a diff as it looks like a hardware issue here but worth a try.

---

