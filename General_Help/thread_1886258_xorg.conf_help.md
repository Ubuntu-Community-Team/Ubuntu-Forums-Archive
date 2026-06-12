---
title: "xorg.conf help"
date: 2011-11-24
forum: General Help
---

### Post by Bryan334 on 2011-11-24
This is a follow up thread..
I reinstalled Ubuntu, I installed my drivers, and then I went to check my Xorg.conf file and this is all it has...
 	

 	 		 			 [PHP]
Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection  
[/PHP]
My main  problem is that I'm having the same problem as last time. My monitor  refresh rate has been set wrong again I think, and I need to fix and add some resolutions that weren't detected. I also want to enable cool bits.

---

### Post by ptrakk on 2011-11-24
what's your card?

---

### Post by Bryan334 on 2011-11-24
> **ptrakk said:**
> what's your card?
It's an Nvidia GeForce 7300 SE/7200 GS.

---

### Post by ptrakk on 2011-11-24
did you get the drivers off the nvidia site? i would get those instead of the apt-get ones. once you download it hit ctrl+alt+1 then ctrl+c. run 'chmod +x ~/Downloads/NV*' then run '~/Downloads/NV*' when that gets done 'startx'

also you could also try the command 'nvidia-xconfig' that generates xorg.conf.

---

### Post by angryfirelord on 2011-11-24
If you installed it through Ubuntu's repository (the Additional Drivers tool), then you should have the nvidia-settings tool. Open up a terminal and type this:
```
sudo nvidia-settings
```
Go to the monitor information, set the refresh rate, and then tell it to save to the xorg.conf file. It should then retain your settings.

---

### Post by Bryan334 on 2011-11-24
> **ptrakk said:**
> did you get the drivers off the nvidia site? i would get those instead of the apt-get ones. once you download it hit ctrl+alt+1 then ctrl+c. run 'chmod +x ~/Downloads/NV*' then run '~/Downloads/NV*' when that gets done 'startx'

also you could also try the command 'nvidia-xconfig' that generates xorg.conf.
Thanks for the help, 'sudo nvidia-xconfig' worked. All the missing data has been filled. And also thanks for trying to help with installing drivers directly from nvidia website. But I've been having trouble simply killing x server. Well, god bless.

---

