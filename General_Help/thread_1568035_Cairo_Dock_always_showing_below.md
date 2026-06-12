---
title: "Cairo Dock always showing below"
date: 2010-09-04
forum: General Help
---

### Post by atscott01 on 2010-09-04
I've been having problems with Cairo dock always showing below other windows. I have tried launching it with cairo-dock --keep-above and cairo-dock -a but to I have had no success. Even editing the settings from the configure to be "always on top" does not work. 

It was working before where it would appear above when I put the cursor at the bottom of the screen, but it isn't anymore, for whatever reason.

---

### Post by krishnandu.sarkar on 2010-09-04
Well...I also faced some similar and other problems with Cairo Dock. Got fed-up and uninstalled it.

---

### Post by atscott01 on 2010-09-04
I'm on the verge of doing the same. Cairo-dock was so pretty...

---

### Post by borth92 on 2010-09-04
right click on the dock and go to: cairo-dock>configure>visability. then change the settings to however you want it to act

---

### Post by borth92 on 2010-09-04
sorry didnt see you already tried that. Try using without opengl....it is buggy

---

### Post by atscott01 on 2010-09-04
> **borth92 said:**
> right click on the dock and go to: cairo-dock>configure>visability. then change the settings to however you want it to act

I have already set it to "al -- oh hey, would you look at that. It's working now. Interesting.

Thank you

---

### Post by borth92 on 2010-09-04
yea Cairo dock can be buggy...the new beta version is actually much better. if you want the beta...type the following into a terminal:
sudo add-apt-repository ppa:cairo-dock-team/weekly

---

### Post by atscott01 on 2010-09-04
> **borth92 said:**
> yea Cairo dock can be buggy...the new beta version is actually much better. if you want the beta...type the following into a terminal:
sudo add-apt-repository ppa:cairo-dock-team/weekly

Awesome, thank you very much.

---

### Post by fabounet on 2010-09-07
also be careful to not use fake transparency
fake transparency makes the dock stays below the windows (you can guess why)
PS : the opengl version is not bugy, the drivers are ;-)
"cairo-dock -c" is a good fallback

---

### Post by Darkhorse85 on 2010-09-22
This is a bit late...I'm having the opposite problem, the dock doesn't stay below windows after start up,then I have to re-apply "keep below windows" option and then it works. The same problem occurs after hibernation. Any ideas #-o

---

### Post by Quackers on 2010-09-22
I must say that I like Cairo Dock very much, but it doesn't always do what it's told :-)

---

### Post by fabounet on 2010-09-23
which version ? the latest one (2.2) has just been released

---

