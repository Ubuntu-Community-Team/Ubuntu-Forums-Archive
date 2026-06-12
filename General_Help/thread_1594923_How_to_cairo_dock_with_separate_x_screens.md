---
title: "How to cairo dock with separate x screens"
date: 2010-10-12
forum: General Help
---

### Post by pieman711 on 2010-10-12
I was having some problems getting cairo-dock to run from startup on both screens when using Nvidia separate x screens. Through some googling I came up with this solution and thought I'd share it here in case anyone else is having any similar troubles.
I did this in ubuntu 10.04 but I can't see why it wouldn't work in any other recent version.
The problem I was having was that putting cairo-dock -o in the 'startup applications' only put it on one screen and to get it on the other I'd have to manually click Applications>Accessories>GLX-dock
Not exactly much effort but then I am *very* lazy. Another problem I was having, that I fixed almost as a by-product of this, was that firefox can only run on one X screen at a time. In my initial cairo-dock setup the firefox launcher could only be configured to launch the same profile of firefox and therefore only have it on one screen at a time. There was a way around this but it involved lots of clicks (again... lazy) I found this helped both problems....

**The Fix**
First I made a *very* simple bash script...
Applications>Accessories>gedit Text Editor. 
type (or copy and paste)...

#!/bin/bash
DISPLAY=:0.1 cairo-dock --dir /home/USERNAME/.config/cairo-dock2 -o

into the open window, **changing the USERNAME to be whatever your user name is**
and save it as startup.sh in your home folder (/home/USERNAME/)

Find the shell script it in nautilus (places>Home Folder) right click on it and go to the permissions tab and click on the "allow executing file as a program" box.

Finally go to System>Preferences>startup applications and click 'add'
Put the name and comment as whatever you want and in the command box type:
/home/**USERNAME**/Startup.sh

That's it!
Now when you startup you'll have a dock on each screen and each will be independently configurable. 
If you right click on the firefox launcher on the second screen and go to "modify this launcher" you can change the command to be something like
firefox -P profile2
and then you can have a firefox on each screen, again both separately customisable. 

I hope this helps, sorry if this is a bit basic but I'm still fairly new to Ubuntu and I found this kind of spelling it out step-by-step very handy when I first got started.

---

