---
title: "gdm"
date: 2010-09-04
forum: General Help
---

### Post by flyingsliverfin on 2010-09-04
what happens if i restart gdm? and how do i do it?
i think i did it once and i lost all my configurations, or maybe that was something else. i just dont want to have to redo all my customizations.

---

### Post by DeMus on 2010-09-04
> **flyingsliverfin said:**
> what happens if i restart gdm? and how do i do it?
i think i did it once and i lost all my configurations, or maybe that was something else. i just dont want to have to redo all my customizations.

Why do you want to restart gdm? Is something broken?

---

### Post by flyingsliverfin on 2010-09-04
kind of, sometimes while i wait for my user to finish logging on, i use the tty's 1-6. then when i finish and log off the tty and go to tty7 (where im now logged on) the screen is completely white. but when i click say in the top left where the applications normally are, it still gives me the drop down menu, from where i can launch applications and use them normally. i have no idea what the problem is

---

### Post by sje46 on 2010-09-04
sudo /etc/init.d/gdm restart 

should work :)

If you do it, it'll basically sign you out, and you will have to sign back in.  Save all your files and stuff before you do it.

(Please correct me if I'm wrong...I'm currently using Mint, not Ubuntu)

---

### Post by WorMzy on 2010-09-04
gdm is the GNOME Display Manager, it's responsible for launching Xorg and your gnome-session. When it stops both of these processes, and any other processes that depended on them, are killed off. When it starts again, it relaunches Xorg and displays the login screen.

To debug your white screen problem, it may be a good idea to stop gdm and start xorg manually. You can do this by running
```
sudo /etc/init.d/gdm stop
```
or possibly
```
sudo service gdm stop
```
depending on the version of Ubuntu you're running.

After that, start xorg manually by running
```
xserver
```
or
```
xinit
```

It's been a while since I launched xorg this way, but I believe that the tty used to launch it should act as stdout for the duration of your xsession; any problems that occur may be printed out to the tty, and you can use this output to determine where the problem is.

---

