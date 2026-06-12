---
title: "Plymouth Background during Bootup"
date: 2010-05-05
forum: General Help
---

### Post by aniruddha on 2010-05-05
Hello all. I've been using Lucid for the last couple of days now and its pretty cool. Except for this plymouth. Aside from the NVIDIA driver issues (which I figured out thanks to the forum), I have very little technical problems now. 

I was wondering though, whether it is possible to change the background (either replace it entirely or change just the colour) during boot. I've tried the themes (from Synaptic) and have not really liked anything that much. I would love to keep the default ubuntu boot screen, but that godsd***** purple colour is really annoying. So, does anyone know how to change that bit?

Thanks a ton. Apologies if I've missed a thread already dealing with this issue, but I couldn't seem to find anything.

---

### Post by sunk8 on 2010-05-05
> **aniruddha said:**
> Hello all. I've been using Lucid for the last couple of days now and its pretty cool. Except for this plymouth.
I was wondering though, whether it is possible to change the background (either replace it entirely or change just the colour) during boot. I've tried the themes (from Synaptic) and have not really liked anything that much. I would love to keep the default ubuntu boot screen, but that godsd***** purple colour is really annoying. So, does anyone know how to change that bit?
Thanks a ton. Apologies if I've missed a thread already dealing with this issue, but I couldn't seem to find anything.

Yup, you can configure it boot easily.
There are two things that you might wanna change:

1] The Boot Splash Theme...
Simply go to synaptic and search for 'plymouth'.
There are a variety of themes available here. Install the ones you wanna try.
Once that's done, open a Terminal and type:
sudo update-alternatives --config default.plymouth
Choose the theme that you want to try. See how it works. You can use the same command to change the plymouth boot theme again.
):P
2] The GDM Login Screen.
Go to a terminal and type:
sudo -u gdm dbus-launch gnome-appearance-properties
This will open the 'Appearance Preferences' window for the root user.
Any changes made here will affect the login screen.
Simply change the background to get rid of the 'purple' one.
You can add more backgrounds to the 'root' user's account too, by copying it into the root folder...

---

### Post by sunk8 on 2010-05-05
You might also want to use the Ubuntu Satanic boot screen.
It's wicked... :guitar:
Go to ubuntusatanic.org for more info...

---

### Post by aniruddha on 2010-05-05
Umm. Thanks sunk8. However, as I said, I have tried out the various themes and not really liked any. All I want to do is change the background for the default theme (or any theme for that matter). 

With respect to changing the GDM, I really don't want to change the appearance properties. And Ubuntu Tweak allows me to change the background for the login screen with no issues. All I want to do is change the background for a theme during boot.

Thanks for your suggestions though. Good stuff.

---

### Post by iumentum on 2010-06-17
This explains how to install a simple wallpaper in Plymouth as well as how to manually install your a theme:
[http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html)

BTW, I really dislike Plymouth at this point. Why roll out such an immature boot splash when there's much more stable and developed modules...uslpash, xsplash, grub2 graphical boot, etc... 

And you know what happens if you try to remove Plymouth from the package manager? Half your system goes with it. At least wait till Plymouth is more developed and tested before including it as the default boot splash I say...

---

### Post by chudder on 2010-06-20
> **sunk8 said:**
> Yup, you can configure it boot easily.
There are two things that you might wanna change:

1] The Boot Splash Theme...
Simply go to synaptic and search for 'plymouth'.
There are a variety of themes available here. Install the ones you wanna try.
Once that's done, open a Terminal and type:
sudo update-alternatives --config default.plymouth
Choose the theme that you want to try. See how it works. You can use the same command to change the plymouth boot theme again.
):P
2] The GDM Login Screen.
Go to a terminal and type:
sudo -u gdm dbus-launch gnome-appearance-properties
This will open the 'Appearance Preferences' window for the root user.
Any changes made here will affect the login screen.
Simply change the background to get rid of the 'purple' one.
You can add more backgrounds to the 'root' user's account too, by copying it into the root folder...

Wonderful!  Step 2 is exactly what I was looking for.  Thank you very much!

---

### Post by sunk8 on 2010-06-22
> **chudder said:**
> Wonderful!  Step 2 is exactly what I was looking for.  Thank you very much!

You're welcome brother Chudder...

---

### Post by Cavsfan on 2010-06-22
> **aniruddha said:**
> Umm. Thanks sunk8. However, as I said, I have tried out the various themes and not really liked any. All I want to do is change the background for the default theme (or any theme for that matter). 

With respect to changing the GDM, I really don't want to change the appearance properties. And Ubuntu Tweak allows me to change the background for the login screen with no issues. All I want to do is change the background for a theme during boot.

Thanks for your suggestions though. Good stuff.

If you mean the bootup grub2 screen. check my sig.
I can help more if you're interested,

---

### Post by Cavsfan on 2010-06-22
I have a huge 28 " monitor and have a 1920 x 1200 grub2 customized screen that displays upon boot.
You can set it to whatever you native display is on your monitor.

---

### Post by spamless on 2010-12-07
> **aniruddha said:**
> Umm. Thanks sunk8. However, as I said, I have tried out the various themes and not really liked any. All I want to do is change the background for the default theme (or any theme for that matter). 

With respect to changing the GDM, I really don't want to change the appearance properties. And Ubuntu Tweak allows me to change the background for the login screen with no issues. All I want to do is change the background for a theme during boot.

I just found this and applied it in Lucid with great results.  I used the same choices the author did.

[http://www.khattam.info/howto-change-ubuntu-pinkpurple-plymouth-boot-screen-to-any-color-you-like-2010-11-09.html#comment-108482029](http://www.khattam.info/howto-change-ubuntu-pinkpurple-plymouth-boot-screen-to-any-color-you-like-2010-11-09.html#comment-108482029)

The only think I still want to do is change the login splash from its purple.  I think that will be easier.

---

### Post by mlupton on 2010-12-07
I've been trying to do the same thing on the ubuntu bootup, but for some reason my nVidia graphics card caused everything to just have this ugly text based look rather than the normal startup that I'm used to seeing on other ubuntu computers. I tried editing plymouth myself but the resolution was all messed up and there was a giant ubuntu start up logo (but it was working right). So I changed the resolution again in hopes to correct it, but now I get an error prompt asking me if I want to start ubuntu in low-res mode, but when I click it nothing happens. Would uninstalling and reinstalling grub 2 from a live cd fix the problem, or do I have to do something drastically different? Any help would be much appreciated. I made my own thread, but I thought it would be better to post to a thread that had a similar problem solved.

---

### Post by Cavsfan on 2010-12-08
> **mlupton said:**
> I've been trying to do the same thing on the ubuntu bootup, but for some reason my nVidia graphics card caused everything to just have this ugly text based look rather than the normal startup that I'm used to seeing on other ubuntu computers. I tried editing plymouth myself but the resolution was all messed up and there was a giant ubuntu start up logo (but it was working right). So I changed the resolution again in hopes to correct it, but now I get an error prompt asking me if I want to start ubuntu in low-res mode, but when I click it nothing happens. Would uninstalling and reinstalling grub 2 from a live cd fix the problem, or do I have to do something drastically different? Any help would be much appreciated. I made my own thread, but I thought it would be better to post to a thread that had a similar problem solved.

Here is [[COLOR=blue]_drs305's GRUB2 Basics tutorial and how to re-install GRUB2_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275").
Item number 12 tells you how to uninstall and re-install grub2. Maybe you can just do it the easy way.
Item 13 tells you how to install if via a live cd. However, if you do this, I would advise uninstalling it first.
It seems to always be better to install fresh than to install over a previous install. And you might want to 
make note of the device Ubuntu is installed on before going to the live CD. I mean the **sdXY**. This can be 
derived with **sudo blkid**.
I hope this helps. :D

And if you get it re-installed and everything is back to normal, you might want to check out the tutorial 
in my signature. But, that's up to you.
Good luck! :D

---

### Post by mlupton on 2010-12-08
Thanks for the help, but I don't think I made this clear when I was describing my boot up problems. It actually attempts to start in recovery mode even when i select the correct operating system. When I try to select "Normal Boot" everything just falls apart. Would your grub 2 reinstall help with this problem?

---

### Post by argedion on 2010-12-08
Cavsfan - Your article is very good and complete. I did simplify things a bit for myself though by changing the value of wallpaper to

/boot/grub/splashimages/ and then I named the file bootsplash.jpg. I had set the graphics up to a better resolution than the default of 640x480. My particular graphics card allows me to go up to 1024x768  so now i can save the file i wish to make the bootsplash to that resolution and then run a simple script that i wrote to just change the picture out. (If anything the only thing i may have to go back and adjust would be the font colors which most of my screens are fairly dark anyways 

Here is a copy of the script if anyone else would like to simplify the task.

```
/bin/bash
set -e

####################################################################
#####                   Argedion                               #####    
#####        Wed 08 Dec 2010 06:53:09 PM EST                   #####
#####               File Name: gsplash.sh                      #####
####################################################################
#version: 1.0.0
# A File to change the Grub splash screen by copying file and changeing
#the name of the file I wish to use for the splashscreen to bootsplash.jpg
#
newsplash="$1"
################Start Script####################
sudo cp "{$newsplash}" /boot/grub/splashimages/bootsplash.jpg
```
Happy splash changing

---

### Post by Cavsfan on 2010-12-09
> **mlupton said:**
> Thanks for the help, but I don't think I made this clear when I was describing my boot up problems. It actually attempts to start in recovery mode even when i select the correct operating system. When I try to select "Normal Boot" everything just falls apart. Would your grub 2 reinstall help with this problem?

I believe reinstalling *should* fix your problem. If it does not simply post a reply in drs305's thread with what the 
problem is and what you have done to correct it. You should get a fairly quick response.

I honestly think you should try the reinstall grub option first as I think that should fix it. I accidentally deleted 
all of my kernels a while back and was able to reinstall them via drs305's link with the live cd. So, you could try 
removing grub and reinstalling it in recovery mode if that is all you can get to and if the reinstall fails, do it 
through the live cd.

---

### Post by Cavsfan on 2010-12-09
> **argedion said:**
> Cavsfan - Your article is very good and complete. I did simplify things a bit for myself though by changing the value of wallpaper to

/boot/grub/splashimages/ and then I named the file bootsplash.jpg. I had set the graphics up to a better resolution than the default of 640x480. My particular graphics card allows me to go up to 1024x768  so now i can save the file i wish to make the bootsplash to that resolution and then run a simple script that i wrote to just change the picture out. (If anything the only thing i may have to go back and adjust would be the font colors which most of my screens are fairly dark anyways 

Here is a copy of the script if anyone else would like to simplify the task.

```
/bin/bash
set -e

####################################################################
#####                   Argedion                               #####    
#####        Wed 08 Dec 2010 06:53:09 PM EST                   #####
#####               File Name: gsplash.sh                      #####
####################################################################
#version: 1.0.0
# A File to change the Grub splash screen by copying file and changing
#the name of the file I wish to use for the splashscreen to bootsplash.jpg
#
newsplash="$1"
################Start Script####################
sudo cp "{$newsplash}" /boot/grub/splashimages/bootsplash.jpg
```Happy splash changing


Thanks, that looks like a handy script!  You could add **sudo update-grub** to the end of it and if your new image name displays 
you will know it was successful.

EDIT: While sudo update-grub will need to be entered for your new image to take effect, under your scenario, the image name 
will not change, so what I said above will not apply. It will display "bootsplash.jpg found" regardless.

---

### Post by soad6 on 2010-12-09
Has anyone found an easy way to change the splash screen from that horrible purple load up?? I've tried to change it like Link on the first page said through changing stuff terminal wise and other and still no luck, reboot and the thing came up purple still. Also what happened to the boot loader splash screen we had back in like 9.04 and 9.10 those even looked alot better then this horrible thing. If anyone can help me change the splash screen to just a glowing picture of the ubuntu logo or a glowing picture of Tux I would appreciate it much. Thank you in advance.

---

### Post by Cavsfan on 2010-12-09
> **soad6 said:**
> Has anyone found an easy way to change the splash screen from that horrible purple load up?? I've tried to change it like Link on the first page said through changing stuff terminal wise and other and still no luck, reboot and the thing came up purple still. Also what happened to the boot loader splash screen we had back in like 9.04 and 9.10 those even looked alot better then this horrible thing. If anyone can help me change the splash screen to just a glowing picture of the ubuntu logo or a glowing picture of Tux I would appreciate it much. Thank you in advance.

Have you tried Ubuntu Tweak > Login Settings? That should be where you can change this screen. I haven't tried in a while.
The last time I tried, it changed it there, but didn't change the login screen for some reason.

---

### Post by soad6 on 2010-12-10
Thats regarding the Login Screen... maybe I wasn't clear I want to change the purple screen with the word ubuntu with the logo with the loading dots ( the plymouth thing) to the orginal ubuntu logo boot screen in 9.10 . Not sure if that was Grub2 or what back then just my issue is that after trying to change the screen by any possible way even installing packages for themes for plymouth from synaptic that after reboot still have ugly purple screen with word ubuntu and ubuntu logo. Thank you again

---

### Post by Cavsfan on 2010-12-10
> **soad6 said:**
> Thats regarding the Login Screen... maybe I wasn't clear I want to change the purple screen with the word ubuntu with the logo with the loading dots ( the plymouth thing) to the orginal ubuntu logo boot screen in 9.10 . Not sure if that was Grub2 or what back then just my issue is that after trying to change the screen by any possible way even installing packages for themes for plymouth from synaptic that after reboot still have ugly purple screen with word ubuntu and ubuntu logo. Thank you again

The purple screen with the 4 dots rarely even appears for me anymore. It might appear for a second or two and then gone.
I did change the picture when you login via Ubuntu Tweak, but it did not change it when I boot up. I just looked in Ubuntu 
tweak and it shows the picture is changed, but the same old purple screen shows asking to login. I have seen some threads 
where people messed with the Plymouth screen you are talking about and they ended up needing help just to boot into 
Ubuntu after that. I will just live with it rather than take a chance on messing it up.

But, I have a nice conky on the right side that shows core temps, core processor percentage in use, RAM and 
disk usage, Network usage and weather that is on a 15 second delay upon startup or else it will display over top 
of anything else and I end up waiting on it to start up after boot up. It is fast!!!

---

