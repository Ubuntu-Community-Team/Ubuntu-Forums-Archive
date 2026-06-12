---
title: "Maverick Meerkat on Celeron R?"
date: 2011-04-03
forum: General Help
---

### Post by meddyuk on 2011-04-03
Hi there.

I've just installed 10.10 netbook on my Fujitsu Siemens Amilo Pro, Intel Celeron M 390 / 1.7 GHz with 700mb of ram.

Unfortunately the graphics are very blocky if that makes any sense. In fact the screen resolution is bigger than it should be for the monitor and whenever i hover my mouse of the left hand side of the toolbar the screen goes black and re-appears. I got a feeling that this has to do with my onboard graphics card VIA UniChrome Pro Shared Video Memory (UMA).

Do i have to give ubuntu up as a bad job on this laptop or can this issue be rectified.

---

### Post by meddyuk on 2011-04-04
When hovering with mouse over menu bar, the full screen changes to  default coloured back ground shortly and then back to normal (as after  start-up) again. And that each time the mouse is over any of the  (default) icons on the menu bar. 



  I am not able to select any icon. No left or right click works on  icons or anywhere on the menubar apart from the left top small icon,  white Ubuntu logo, and the right top small icons for WiFi, sound, mail,  shut-down etc. Those icons work. 



  I tried re-installation again and all patches are downloaded. Same  problem. Problem is that I can't enter commands either to reduce e.g.  the swappiness (if that would be of any help). 
  

I cannot read any of the lables for any of the icons either. I manage to get into settings ( icon on left with sissors) after some great persistence, but cannot read the labels to the icons, as they are all white blocks.

---

### Post by mastablasta on 2011-04-04
as you already guessed your problems are caused by graphics card which is responsible for drawing everything you see on the monitor. If the card doesn't have propper drivers it will not function. you could try searching for linux driver for your card on internet. i am not familiar with it so i can't offer much help i am affraid.
 
You can access text mode command line in gnome with crtl+alt+F1  to F7 i think.
 
however it iwll be annoying to type any more complicated commands.
 
you could try turning of desktop effects if they are maybe on and causing the mayhem.

---

### Post by Mark Phelps on 2011-04-04
The VIA Unichrome is the problem.  There have been numerous posts in the Audio & Video subforum and none of them are promising.  You might have to go back several years to find an Ubuntu distro with decent VIA Unichrome video drivers.

---

### Post by meddyuk on 2011-04-05
Cheers Guys thanks for that reply. I thought as much. I did try and download some drivers for the internet, but the site stated for pre Ubuntu 8.

Dont suppose you know where i can get an old ubuntu distro from? Is it worth it?

---

### Post by mastablasta on 2011-04-06
> **meddyuk said:**
>  
Dont suppose you know where i can get an old ubuntu distro from? ?
It will be in the archives.
 
> Is it worth it?
 No, i don't think so. You might experience other driver issues with older distro. No tto mention it won't be supported.

---

### Post by meddyuk on 2011-04-08
Just tried Puppy Linux and im using that from a USB stick. I've tried installing Lubuntu but had snags installing.

I really want to get Ubuntu 10.10 working as i've had XP on it previously but had a virus. Shouldn't see why Meerkat shouldnt work!

I've been looking into the Open Chrome drivers and wondered if anyone had any experience installing these?

---

### Post by meddyuk on 2011-04-12
Ok Team!
 
I managed to get the screen resolution to 1200 x 768 by pasting the attached .txt file and renaming it .conf in the x11 folder. THis has sorted out the resolution, however, the menu bar on the left still disappears when i hover my mouse over it and the menu/icons have no writing, just blocks. The screen is very jumpy when ever i move my mouse.
 
I dont want to give up! I love ubuntu and run it on my Desktop, and really want to get this issue sorted on my V2030 laptop.
 
I dont know if i have installed the via graphics driver properly. Im not even sure ive installed the right one.
 
Is there a way i can change my desktop effects so that at least the menu bars will display writing?
 
Please someone, must have a clue how to sort this issue!!!

---

### Post by jerome1232 on 2011-04-12
I think part of your problem is unity, it's 3d only right now.

Try logging in an Ubuntu Desktop Session, After you select your user down at the bottom is a drop down box with a list of different sessions, this should bring up a regular gnome environment with no 3d extra's. Unfortunately it's not optimized for a small screen like unity is but everything should work.

---

### Post by meddyuk on 2011-04-12
Thats Brilliant. Can't believe thats all i had to do. The screen has also maintained the correct resolution. Looks like this might be a winner. All i gotta do now is tweak.
 
Cheers mate.

---

### Post by meddyuk on 2011-04-12
Ok Next problem. Gotta felling there will be more to come.
 
I've just opening Open Office and the whole laptop has froze. The mouse doesnt move and i'm having to turn off and turn on again. It did it this morning in Unity, when opening and installing updates in the software centre. I got round this by sudo apt-get update in terminal.
 
Whats the problem now with the whole freezing issue?

---

### Post by Script Warlock on 2011-04-12
> **meddyuk said:**
> Ok Next problem. Gotta felling there will be more to come.
 
I've just opening Open Office and the whole laptop has froze. The mouse doesnt move and i'm having to turn off and turn on again. It did it this morning in Unity, when opening and installing updates in the software centre. I got round this by sudo apt-get update in terminal.
 
Whats the problem now with the whole freezing issue?

have you checked the /var/log for some errors?

---

### Post by meddyuk on 2011-04-12
No which log in /Var/log do i check and what am i looking for?

---

### Post by Script Warlock on 2011-04-12
of course you have to check what causes the freezing it might be something like hardware or OS or kernel or whatever that was.. check on /var/log/messages at the time it occurs.

---

### Post by meddyuk on 2011-04-12
Ok...i'll check that out next time it does it. So far ive managed to open them with no problems as yet.
 
Next problem......
 
If i install updates it just freezes until I move the mouse. Infact come to think of it, on boot up it wont do anything until i move the mouse.
 
I've set the clock and thats running very slow.
 
I wondered if it had anything to do with this [post]("http://ubuntuforums.org/showthread.php?t=1619219") and if so how do i change the command kernel?
 
BTW thanks for your assisted help in trying to get this issue sorted!

---

### Post by meddyuk on 2011-04-12
NOOOOOO!!!!!!!!
 
Just updated my boot/grub file and now it boots to a black screen. (*&^%!!)
 
I take it i have to do a re-install?

---

### Post by Script Warlock on 2011-04-12
darn what have you done a minute ago to your boot option?

---

### Post by meddyuk on 2011-04-12
what a wally!
 
I thought that i may have a go at solving the problem myself by doing the following:
 
sudo pico /etc/default/grub

change

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapci_timer clocksource=jiffies"

save changes

sudo update-grub

reboot

but ive just realised that i bet it should say nolapic instead of pci !!!!!

---

### Post by meddyuk on 2011-04-13
Ok went for a re-install and am back to normal, well normal for this setup anyhoo!
 
I'm now at the stage where i am happy now with the screen resolution. That is now at 1200x768.
 
I've also changed from unity to desktop edition, which improves the laptops viewing and there is no more joltyness.
 
Although im stuck with the same problem of freezing. My laptop seems so freeze when doing things like writing in terminal, or installing updates and will only seem to wake up when i move the mouse. Its exactly the same as [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/657990](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/657990)
 
I've gone and done this:
 
sudo pico /etc/default/grub

change

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic_timer clocksource=jiffies"

save changes

sudo update-grub

reboot

But its not changed a thing. any ideas on how to resolve the freezing issue? does clocksource=jiffies go on the same line as nolapic?

---

