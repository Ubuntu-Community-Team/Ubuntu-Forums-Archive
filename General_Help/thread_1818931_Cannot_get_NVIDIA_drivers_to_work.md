---
title: "Cannot get NVIDIA drivers to work"
date: 2011-08-05
forum: General Help
---

### Post by Zuar on 2011-08-05
[COLOR="Red"]***EDIT - see bottom of post***[/COLOR]

I've spent hours and hours today trying to sort out these video drivers. I initially tried to install the drivers through Ubuntu but the drivers it installed haven't made any difference. They are 'active but not currently in use'. I downloaded the latest Linux drivers from the NVIDIA website and tried to install as root, but got an error saying that X server is running and I should turn it off. I have tried going into command line and typing init 1, which takes me to an Ubuntu loading screen where the system crashes. I have tried the same with init 2 and 3 but these don't do anything. I have also tried typing '/etc/init.d/gdm stop', but this returns the error: 

"Rather than involking init scripts through /etc/init.d, use the service(8) utility, e.g. service gdm stop

Since the script you are attempting to involk has been converted to an Upstart job, you may also use the stop(8) utility e.g. stop gdm"

When I type 'service gdm stop' I receive the error "stop: unknown instance". If I try 'service /etc/init.d/gdm stop I receive the error "/etc/init.d/gdm: unrecognised service". 'stop gdm' also returns the "stop: unknown instance" error.

I'm new to Ubuntu and this is really confusing! I have been trying to find a way around this for hours. I can't use the native resolution at the moment and it's getting pretty annoying. I'm running Ubuntu 64bit. Any help would be greatly appreciated. I have been reading a lot of similar threads but can't seem to get around these little errors.

Thanks
-Zuar
[COLOR="Red"]

EDIT: It seems as though shortly after writing this the driver let me install it. **However**, I now have even fewer resolutions available (2 which are incredably low). Is this a problem with OpenGL? I was advised not to install it as I'm using a 64bit system.[/COLOR]

---

### Post by moorhead98 on 2011-08-05
> **Zuar said:**
> [COLOR=Red]***EDIT - see bottom of post***[/COLOR]

I've spent hours and hours today trying to sort out these video drivers. I initially tried to install the drivers through Ubuntu but the drivers it installed haven't made any difference. They are 'active but not currently in use'. I downloaded the latest Linux drivers from the NVIDIA website and tried to install as root, but got an error saying that X server is running and I should turn it off. I have tried going into command line and typing init 1, which takes me to an Ubuntu loading screen where the system crashes. I have tried the same with init 2 and 3 but these don't do anything. I have also tried typing '/etc/init.d/gdm stop', but this returns the error: 

"Rather than involking init scripts through /etc/init.d, use the service(8) utility, e.g. service gdm stop

Since the script you are attempting to involk has been converted to an Upstart job, you may also use the stop(8) utility e.g. stop gdm"

When I type 'service gdm stop' I receive the error "stop: unknown instance". If I try 'service /etc/init.d/gdm stop I receive the error "/etc/init.d/gdm: unrecognised service". 'stop gdm' also returns the "stop: unknown instance" error.

I'm new to Ubuntu and this is really confusing! I have been trying to find a way around this for hours. I can't use the native resolution at the moment and it's getting pretty annoying. I'm running Ubuntu 64bit. Any help would be greatly appreciated. I have been reading a lot of similar threads but can't seem to get around these little errors.

Thanks
-Zuar
[COLOR=Red]

EDIT: It seems as though shortly after writing this the driver let me install it. **However**, I now have even fewer resolutions available (2 which are incredably low). Is this a problem with OpenGL? I was advised not to install it as I'm using a 64bit system.[/COLOR]

I had the same problem. Could you tell me the graphics card? 
When i experienced the problem, it was that the graphics chip i had was blacklisted. It gave me the same message (installed but not in use), and there were a couple of workarounds I had to use. 
So yeah, what is the graphics card?

---

### Post by Zuar on 2011-08-05
-Disregard this-

---

### Post by Zuar on 2011-08-05
> **moorhead98 said:**
> I had the same problem. Could you tell me the graphics card? 
When i experienced the problem, it was that the graphics chip i had was blacklisted. It gave me the same message (installed but not in use), and there were a couple of workarounds I had to use. 
So yeah, what is the graphics card?

Geforce 9600GS :)

---

### Post by moorhead98 on 2011-08-05
> **Zuar said:**
> Geforce 9600GS :)

Hmmm... Doesnt look like its blacklisted.
Are you trying to do anything in particular? like games or unity? Try downloading some 3d game from ubuntu software center (like supertuxkart) and see if it works (if it doesnt it should be just a black screen) 
If its unity your after, and you can run 3d programs (like supertuxkart), then there is a quick workaround to get unity rolling.

---

### Post by Zuar on 2011-08-05
> **moorhead98 said:**
> Hmmm... Doesnt look like its blacklisted.
Are you trying to do anything in particular? like games or unity? Try downloading some 3d game from ubuntu software center (like supertuxkart) and see if it works (if it doesnt it should be just a black screen) 
If its unity your after, and you can run 3d programs (like supertuxkart), then there is a quick workaround to get unity rolling.

My biggest issue is that I can't get my native resolution. I was hoping that installing the drivers would fix that issue. Now I just get a blank screen on start-up... I can use ctrl alt f1 to get into command line and I've tried stuff like /etc/init.d/gdm restart, startx and I've also tried pressing 'ctrl alt backspace' - this just displays a blinking like on the screen and displays the keys I press (something like ]^H, not exactly that though)

---

### Post by moorhead98 on 2011-08-05
> **Zuar said:**
> My biggest issue is that I can't get my native resolution. I was hoping that installing the drivers would fix that issue. Now I just get a blank screen on start-up... I can use ctrl alt f1 to get into command line and I've tried stuff like /etc/init.d/gdm restart, startx and I've also tried pressing 'ctrl alt backspace' - this just displays a blinking like on the screen and displays the keys I press (something like ]^H, not exactly that though)

Is it sort of like the picture isnt as big as the screen?

---

### Post by Zuar on 2011-08-05
> **moorhead98 said:**
> Is it sort of like the picture isnt as big as the screen?

No, it should run at 1920x1080 but the max resolution is way lower. But right now I can't even log in because the whole screen is black on start-up.

---

### Post by moorhead98 on 2011-08-05
> **Zuar said:**
> No, it should run at 1920x1080 but the max resolution is way lower. But right now I can't even log in because the whole screen is black on start-up.

How in the world did you do that? Not to be offensive, just asking

---

### Post by Johnb0y on 2011-08-05
[http://www.perpetualpc.net/srtd_resolution.html](http://www.perpetualpc.net/srtd_resolution.html)

not to be mean or anything... :(

---

### Post by Zuar on 2011-08-05
> **moorhead98 said:**
> How in the world did you do that? Not to be offensive, just asking

I turned off gdm and it doesn't want to turn back on...

> **Johnb0y said:**
> [http://www.perpetualpc.net/srtd_resolution.html](http://www.perpetualpc.net/srtd_resolution.html)

not to be mean or anything... :(

I'll look into this once I get past this blank screen stage, thanks :)

---

### Post by moorhead98 on 2011-08-05
> **Zuar said:**
> I turned off gdm and it doesn't want to turn back on...



I'll look into this once I get past this blank screen stage, thanks :)
If you turned off gdm, then you probably cant get anywhere. 
When your computer boots, is it a blank black screen where gdm should be? 
Try hitting enter, and then entering your password. That should log you into the last session (unity, kde, xfce) you were in. if its still a black screen, but you heard your login sound or something, then youre in. then open up the terminal ( control alt T  ) and type in the commands the other persons link suggested.
But if you have nothing, then youre probably screwed. You could try booting into a live cd and reinstalling.

---

### Post by Zuar on 2011-08-05
> **Johnb0y said:**
> [http://www.perpetualpc.net/srtd_resolution.html](http://www.perpetualpc.net/srtd_resolution.html)

not to be mean or anything... :(

This doesn't show the native resolution still, the largest one available is 1024x768. The native res is 1920z1080

---

### Post by pqwoerituytrueiwoq on 2011-08-05
you are better off installing it via a ppa
the 1st command may fail it is just to be on the safe side
```
sudo nvidia-installer --uninstall
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
sudo reboot
```It is possible to do it the way you are trying but the above is a better way
you have to use *nomodeset* in your kernel boot line and close gdm (*sudo service gdm stop*) before you can install it then it will need to be reinstalled after every kernel update

---

### Post by Zuar on 2011-08-05
> **pqwoerituytrueiwoq said:**
> you are better off installing it via a ppa
the 1st command may fail it is just to be on the safe side
```
sudo nvidia-installer --uninstall
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
sudo reboot
```It is possible to do it the way you are trying but the above is a better way
you have to use *nomodeset* in your kernel boot line and close gdm (*sudo service gdm stop*) before you can install it then it will need to be reinstalled after every kernel update

I have done this but and there are a couple more resolutions available now. Still not the native 1080p one though :(

---

### Post by pqwoerituytrueiwoq on 2011-08-05
```
sudo Xorg -configure
cat /etc/X11/xorg.conf
```
post the out put of the second command here
we may be able to force the native resolution
it could be your gpu is not meant to display that big though

---

### Post by wildmanne39 on 2011-08-05
Hi, I wanted to say that the thing about it saying driver active but currently not in use is just a bug if you activated it and you could see the unity desktop then it was working and you just needed to set your resolution with xrandr or xorg file.

Since you have installed drivers from more then one source it is likely that you have at least two installed, and you should open synaptic and if you have more then one installed,uninstall all but one then restart your computer.

You probably will still have to manually set your resolution I did a few months ago. 

Here is a link for setting the xorg if xrandr does not work.
[http://grenage.com/xorg.html](http://grenage.com/xorg.html)

In 11.04 you have to create the new file it is not already created in 11.04.

---

