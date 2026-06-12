---
title: "x server config change - now can't even get to log in screen HELP!"
date: 2011-06-04
forum: General Help
---

### Post by aikitim on 2011-06-04
ok so I upgraded to 11.04, which has gone down like a ton of bricks so far, and went to set up my dual monitors, but when I changed my x server configuration and saved the new xconf file, after my restart I don't even get to a login screen - I get a quick flash of the ubuntu wallpaper then back screen. If i press the power button, i get a few lines of code which disappear before they can be read and the computer shuts down. Can anyone help? Is this just a case of putting a default xconf file into the xconf folder? Right now I'm just running off of a flash drive, so I can't seem to access and edit any files from my actual install to do this. anyone have any insight? If this isn't clear let me know and I'll try to explain it another way. I really need this to work ASAP!!! Thanks

Tim

---

### Post by aikitim on 2011-06-04
ok let's have a more coherent message from me:

I'm running a fresh install of 11.04 narwhal on a dell xps1530m with a nvidia 8600m gt, on default proprietary nvidia drivers. I'm trying to configure the dual screen setup i had running in 10.1, but to no avail. when I attempted to set it up the way I had done originally, when I reset the xserver, it seems xserver cannot re-load and will not detect a display. I can ctl+alt+f1 into a terminal and have tried 

sudo dpkg-reconfigure -phigh xserver-xorg

and

sudo nvidia-xconfig

based on some google searches but to no avail,

also i have looked in vi at the actual /etc/x11/xorg.conf file, but cannot see anything that looks out of the ordinary - any suggestions? I don't really want to reinstall 11.04 for the 7th time today.... thanks

---

### Post by aikitim on 2011-06-04
Back into gui with simple apt-get remove and reinstall of xserver, can anyone help me setting up dual monitors now?

---

