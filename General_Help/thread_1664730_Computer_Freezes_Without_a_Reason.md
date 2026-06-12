---
title: "Computer Freezes Without a Reason"
date: 2011-01-11
forum: General Help
---

### Post by JCM_Pico on 2011-01-11
I there,
 I have an Asus UX-30 running Ubuntu 64-Bit, and it often freeze with no reason... sometimes I have no program running and when I try to move the mouse it wont go any where, the keyboard give me no input and ctrl+alt+del give me nothing.... The only way is to cut off the power...
Is there any way to solve this problem?

---

### Post by kerry_s on 2011-01-11
have you tried disabling composting(effects)?

---

### Post by JCM_Pico on 2011-01-11
Its an idea  :) 
Disable the visual effects done 
Will see if it freezes again
Thank you

---

### Post by JCM_Pico on 2011-01-12
I turn of the visual effects and it stop freezing with normal use...
But when I watch to a video it often freezes, and the only way to get the system back is to switch off the power and restart.... 
Any idea of how can I solve this?

---

### Post by kerry_s on 2011-01-12
video? are you talking about flash?
if so, how did you install it?

i'm using ubuntu 64, i install "ubuntu-restricted-extras" to get all the stuff needed for all media. i have no problems with flash.

---

### Post by JCM_Pico on 2011-01-12
I don't have problems with flash video :), it only freezes when I play movies like an .avi file !!!!
I will give a try to ubuntu-restricted-extras 
Thanks

---

### Post by MARP1961 on 2011-01-12
My freezing problems were connected with the default wi-fi driver that Ubuntu installed. I solved it by installing the original Windows driver for my desktop pc's PCI wi-fi adapter. The driver 'inf.file' was on the install disk that came with the adapter I'd purchased. I used a programme called ndiswrapper to install it. I instantly lost all the annoying freezes that nearly made me go back to Windows.

---

### Post by JCM_Pico on 2011-01-12
> **MARP1961 said:**
> My freezing problems were connected with the default wi-fi driver that Ubuntu installed. I solved it by installing the original Windows driver for my desktop pc's PCI wi-fi adapter. The driver 'inf.file' was on the install disk that came with the adapter I'd purchased. I used a programme called ndiswrapper to install it. I instantly lost all the annoying freezes that nearly made me go back to Windows.

After installing Ubuntu the wi-fi in the laptop didn't have driver. I had to compile the ralink manually... so I doubt that the problem is associated with the wi-fi drivers

---

### Post by JCM_Pico on 2011-01-12
After installing ubuntu-restricted-extras it still freezes when playing a movie :(

Any more ideas?

---

### Post by Trapper on 2011-01-12
My u100.10 32 bit installs were an absolute headache because of freeze ups. Even nautilus froze up when copying anything over 300 MB to another partition, a usb drive, etc. The only way we resolved the freeze up issues here was to revert back to 10.04. We are forgoing utilizing 10.10. It's definitely unreliable here.

---

### Post by kerry_s on 2011-01-12
> Any more ideas?

install "gnome-mplayer" or "vlc" totem sucks for media player.

i use gnome-mplayer with a tweak "-lavdopts skiploopfilter=all" so everything runs smooth on my atom 230 nettop.

---

### Post by tgalati4 on 2011-01-12
Do you have temperature monitors on your cpu and gpu?  Sometimes when playing a video, it will raise the temperature of the graphics processor causing a hard shutdown that the system can't catch in a log file.

There may be settings in the BIOS to set temperature alarms, so at least you get a beep before shutdown.

Then at least you will get a warning.

Also, run the laptop without a battery, if it will boot without one.  Sometimes a bad battery will cause a no-notice, low-voltage shutdown.

---

### Post by no2498 on 2011-01-12
install htop type it in a terminal it tells you how to install it 
after install type htop click enter 
start a video let it run in the back ground
keep an eye on htop see what is running and how hard its hitting things

---

### Post by JCM_Pico on 2011-01-12
> **no2498 said:**
> install htop type it in a terminal it tells you how to install it 
after install type htop click enter 
start a video let it run in the back ground
keep an eye on htop see what is running and how hard its hitting things

Already tryed to monitor htop before, and cant find a pattern that explain the freeze...

I will give a try to gnome-player or vlc and check if works out.... And I haven't been watching to GPU temperature, so I will check this one to :D

Thanks all

---

### Post by JCM_Pico on 2011-01-14
I again :( ....

 gnome-mplayer with the tweak did not work, and the temperature doesn't explain the freeze....
Its getting really annoying, I tried to play the movies in windows and it plays nicely, so its probably an  Ubuntu system problem

Ideas ????

---

