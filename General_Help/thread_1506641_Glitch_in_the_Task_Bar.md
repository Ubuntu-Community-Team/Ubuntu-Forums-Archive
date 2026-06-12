---
title: "Glitch in the Task Bar"
date: 2010-06-10
forum: General Help
---

### Post by SteamInc on 2010-06-10
For some reason randomly my task bar messes up for some reason. Im not sure if many other people have this. but ill provide a picture so you can see it. Some times its even worse, like i get a double account name and double of everything else.

---

### Post by Woody1987 on 2010-06-10
I had that problem, but an update fixed it. Trying updating. If that doesnt fix it, remove the applets and then add them again. This will reset its configuration.

---

### Post by garvinrick4 on 2010-06-10
I have had it quite often but usually on a Alpha install of pre-released version.
I just right click and delete and make a new applet real quick if I do not want to look at it.

---

### Post by bshosey on 2010-06-10
I get this ever once in a while not often but I do get it. I runt this command in terminal

killall gnome-panel

the panels will dis appear and back again with working icons.

---

### Post by jazzman76063 on 2010-08-19
I have been having this problem.  Computer is a macbook pro 7,1 13.3".  I installed the 10.04 8/16 daily build and it is up to date.  

Is it normal to have to killall the panel on a regular basis or could there be some other long term fix?

I did try this process in the terminal to see if it would help, but the issue has still occurred: 
```
gconftool --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```If there is not an alternate fix, does somebody know some way I can do a "scheduled task" to run killall gnome-panel X seconds (I'm thinking 5 or 10 seconds) each time I start/restart Ubuntu?

Thanks

---

