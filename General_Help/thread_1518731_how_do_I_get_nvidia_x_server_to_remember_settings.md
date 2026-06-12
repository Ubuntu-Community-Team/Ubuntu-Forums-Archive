---
title: "how do I get nvidia x server to remember settings"
date: 2010-06-27
forum: General Help
---

### Post by naginalf on 2010-06-27
Ok, I find it very hard to believe that no one else is having this issue, but since I can't seem to find ANYTHING helpful at all, I'm posting the question in hopes of a simple answer.  I'm running 10.04 and have an nvidia 8400gs out to an lcd monitor and a standard tube TV via svideo.  Now I have no problem whatsoever getting the screen resolutions correct and the display to work properly on my TV, but it is, of course overscanned.  There is a handy dandy slider for that in the nvidia x server settings gui which works beautifully, but no matter what I do IT WILL NOT SAVE THAT SETTING.  Now I've seen post after post after blog after blah blah blah, but nothing is helping me SAVE THE OVERSCAN SETTINGS!!!  I've tried saving the nvidia-settings-rc file, but when that file is loaded, it does not change the overscan settings.  I've changed the xinitrc file to include nvidia-settings --config-load-only, but nothing there, even after making the xinitrc file executable.  I would try entering the above command into the startup, but I can never get the command to change the settings I want in terminal, so I doubt it will do anything upon startup.  I've also tried editing the xorg.conf file to include the setting <Option "TVOverScan" "0.9"> under Monitor1 section (TV)  which changes nothing.  WHY IS THIS SO HARD?!!!!

Sincerely frustrated. . .:???:](*,):confused:

---

### Post by stderr on 2010-06-27
To save most settings in the nvidia-settings GUI, you have to run it as root, because it has to write to /etc/X11/xorg.conf. I.e., open up a terminal and type:

```
gksudo nvidia-settings
```

Hope that helps.

---

### Post by naginalf on 2010-06-27
Nope, tried that before, and tried it again just now, but still nothing sticks.

---

### Post by dino99 on 2010-06-27
have seen lot of complaints with this card over forums

[http://www.google.fr/search?as_q=8400gs%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.fr/search?as_q=8400gs%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by naginalf on 2010-06-27
These sliders must be changing a setting somewhere or they would go away as soon as the gui is closed.  What file is this setting stored in and how do I change it?  I see nothing in either xinitrc, xorg.conf, or .nvidia-settings-rc.  I think that this setting is either not being written to the xorg file, and/or when I insert the command into it, it does not change the appropriate setting in the driver (sorry, my vernacular may be off there, but you understand my meaning).  If nothing else, is there some script that I can write to execute upon startup that will change the overscan settings in the nvidia driver?

---

### Post by stderr on 2010-06-27
I'm running 9.10 so it may not be quite the same, but if I look in ~/.nvidia-settings-rc amongst all the configuration parameters I see:

```
0/OverscanCompensation[CRT-1]=0
0/OverscanCompensation[DFP-0]=0
```

If those values are being set to whatever you set the slider to in nvidia-settings, then you should be able to run this after a reboot:

```
nvidia-settings -l
```

But as you say that doesn't work... so do you have the OverscanCompensation entries in your .nvidia-settings-rc? Or are they named something different like 0/TVOverScan[CRT-0]=0...

The gist being that I think if you set the line correctly in .nvidia-settings-rc and automatically execute nvidia-settings -l after each reboot, I think it should work.

---

### Post by mal209 on 2010-08-15
hey everyone, im new here, and have been having the same problem...

i saved ~/.nvidia-settings-rc and have the proper "tv overscan" line set to 56 in that file.

if i run: 
  nvidia-settings -l

i get about 30 errors with this format:
  ERROR: unable to assign attribute *random nvidia-settings-rc parameter* specified on line *number* of configuration file '/home/**/.nvidia-settings-rc' (no Display connection).

I am running SLI 8500 (nvidia) cards to a Sharp HD TV via DVI (everything is working great except overscan which resets ever time i log off).

i should also note that running "nvidia-settings -l" does not set the overscan, but running the gui nvidia settings does... just annoying to have to reset each time..

any help would be greatly appreciated... 
-Michael.

---

### Post by disparil on 2010-09-10
I have the same problem ](*,)

> Unable to assign attribute OverscanCompensation specified on line 50 of configuration file '/root/.nvidia-settings-rc' (no Display connection).

I tested by running nvidia-settings as root, but does not solve anything. It looks like nvidia-settings can not save or recover these parameters.

Has anyone found a solution?


thanks!

PS: My version of Ubuntu is 10.04, and I've tried with "sudo" and "sudo su"

---

### Post by soryu on 2010-09-11
> **mal209 said:**
> hey everyone, im new here, and have been having the same problem...

i saved ~/.nvidia-settings-rc and have the proper "tv overscan" line set to 56 in that file.

if i run: 
  nvidia-settings -l

i get about 30 errors with this format:
  ERROR: unable to assign attribute *random nvidia-settings-rc parameter* specified on line *number* of configuration file '/home/**/.nvidia-settings-rc' (no Display connection).

I am running SLI 8500 (nvidia) cards to a Sharp HD TV via DVI (everything is working great except overscan which resets ever time i log off).

i should also note that running "nvidia-settings -l" does not set the overscan, but running the gui nvidia settings does... just annoying to have to reset each time..

any help would be greatly appreciated... 
-Michael.









same thing. this is half of them:eek:

 ________________________________________
/ You will be married within a year, and \
\ divorced within two.                   /
 ----------------------------------------
  \
   \   \_\_    _/_/
    \      \__/
           (oo)\_______
           (__)\       )\/\
               ||----w |
               ||     ||
mint@mint-desktop ~ $ nvidia-settings

ERROR: Cannot open display 'mint-desktop:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 20 of
       configuration file '/home/mint/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 21 of
       configuration file '/home/mint/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 22 of
       configuration file '/home/mint/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 23 of
       configuration file '/home/mint/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 24 of
       configuration file '/home/mint/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 25 of
       configuration file '/home/mint/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 26 of
       configuration file '/home/mint/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 27 of
       configuration file '/home/mint/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 28 of
       configuration file '/home/mint/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 29 of configuration
       file '/home/mint/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 30 of
       configuration file '/home/mint/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GammaCorrectedAALines specified on line 31 of
       configuration file '/home/mint/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 32 of
       configuration file '/home/mint/.nvidia-settings-rc' (no Display
       connection).

running nvidia-settings i can apply & save settings.
running gksudo nvidia-settings automatically applies saved settings.

---

### Post by In2Deep on 2010-09-19
I had the same problem with errors when trying to fix overscan with "nvidia-settings -l". Continually had to run gksu nvidia-settings to reload the Overscan Compensation setting.

I managed a workaround by adding the following to the SYSTEM->PREFERENCES->STARTUP APPLICATIONS

```
nvidia-settings -a [gpu:0]/OverscanCompensation[DFP-1]=60
```

You might have to change the gpu setting, display name, and the compensation amount. I just copied what was in the nvidia-settings-rc file and changed the display call-out to one that worked.

My setup:

Ubuntu 10.04
GeForce 9300
driver 195.36.31
Pioneer 5072HD via HDMI

Hope this helps :)

---

### Post by ben2talk on 2010-11-07
nvidia-settings -a [gpu:0]/OverscanCompensation[DFP-1]=60

on my system it's

nvidia-settings -a [gpu:0]/OverscanCompensation[TV-0]=85

Thanks for the help there.

---

