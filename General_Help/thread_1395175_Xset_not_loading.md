---
title: "Xset not loading"
date: 2010-01-31
forum: General Help
---

### Post by RFXCasey on 2010-01-31
Hi, my mouse is too slow for me even on the highest setting in Ubuntu so I have to go into terminal and use xset m 5 1 every time I restart the machine. I have tried making an xsession script and it seems to be loading because if I mess up the syntax in the script I get a complaint an x won't start however my mouse is not being set correctly. The script named .xinitrc is as follows

#!/usr/bin/env bash
xset m 5 1 &
exec gnome-session

I am not 100% sure it is loading when Ubuntu starts but it seems to be when I startx from outside of the desktop environment.

---

### Post by RFXCasey on 2010-02-04
Sorry to whine, really, but what is going on with the support forums lately? More times then not I get absolutely no reply to my posted issues. I don't think I am asking any deeper level of questions lately and can't believe that no one has any knowledge or experience in these particular areas? It's not just here, but seems like everywhere the level of support seems to focus on the much easier problems while skipping over some of the more challenging incidents.

---

### Post by subever on 2010-02-11
well make new script file with your commands, put it in home folder 
and then go to System > Preferences > Startup Applications
add your script file path, for example if it's 
"/home/username/programs/boot.sh"
then the command will be "sh /home/username/programs/boot.sh"

goodluck

---

