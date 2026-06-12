---
title: "Restore ATI open source drivers"
date: 2010-04-22
forum: General Help
---

### Post by gwu777 on 2010-04-22
[FONT=Verdana]Hi there,

In the past few days, I have been testing with the ATI Catalyst drivers. I have made a package from the 9.12. I have found that they were not working the way I want, so i tried to switch back via synaptic. I have removed everything which had to do to "fglrx"

now when I restart, here is the message i get

> UBUNTU is running in low graphic mode
The following error was encountered. You may need to update your configuration to solve this. (EE) failed to load module "fglrx" (module does not exist, 0)For information, it does start in low graphic mode. I have reinstalled the "fglrx" module, but the problem is still the same. If I reinstall the fglrx drivers from synaptic or terminal, I am back with the newer catalyst driver. I cannot switch back to the ubuntu repository one it seem.

I have done the following to try to get the open source back

[/FONT]> sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
sudo apt-get remove --purge fglrx*
[FONT=Verdana]sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg[/FONT][FONT=Verdana]

I still have the same problem. Now I do not have any package installed with "fglrx" I have reconfigured xserver-xorg and it will only start in low graphic mode.

Any help will be appreciated.

[/FONT][FONT=Verdana]

[/FONT]

---

### Post by Yellow Pasque on 2010-04-22
What does /etc/X11/xorg.conf look like?

---

### Post by P4man on 2010-04-22
have you checked your xorg.conf? Maybe there is still a reference to the fglrx in there. Just rename the file?

---

### Post by gwu777 on 2010-04-22
> **Temüjin said:**
> What does /etc/X11/xorg.conf look like?

A mess! Indeed, some mention of fglrx was left in the device section, I changed it for radeon, and my system started again, with the open source drivers.

However, metacity was not running properly (a problem) I already had before. I fixed this problem by loading the prioritary drivers from the ubuntu depot. I tried to to this as I had done before, but the system wasn't able to activate the new drivers. After looking at the log file I found that it was still probably due to my xorg.conf file. I moved it to xorg.conf.bck and restarted the system to force it to create a new xorg.conf.

It worked! A few extra bugs have also been repaired (screen resolution for exemple and metacity started fine). I was then able to activate very normally the proprietary drivers and I now have my effect running again. Despite wasting my morning on this (which is always annoying when I would like things to work first time and Ubuntu always want me to learn new things) I know have a better understanding of screen resolution and pro and cons of the various drivers! I take this as a bonus.

Thank you for your help.

---

### Post by P4man on 2010-04-22
Just for the record; xorg.conf is optional nowadays. you dont need one. But if you do have one, it will get parsed.

---

### Post by gwu777 on 2010-04-22
> **P4man said:**
> Just for the record; xorg.conf is optional nowadays. you dont need one. But if you do have one, it will get parsed.

This is what I thought, and this is why I didn't think about checking the file out. However, when I deleted it, Ubuntu made an other one back. furthermore it stopped me upgrading successfully to the ATI prioritary driver. I never asked for the xorg.conf file, but it is still there. Anyone wanting to explain?

---

