---
title: "Window Manager crash"
date: 2011-12-01
forum: General Help
---

### Post by goodbye-windows(tm) on 2011-12-01
Hi All,

Window Manager shows blank screen instead of listing options relative to window control.

Now, an application opens with the window covering the upper left of the panel screen-so I'm unable to close some programs. The X and the bar to minimize an application is blank, so windows can't be minimized, moved or resized.

This problem happened occasionally in the past, and a quick 'xfce4-session-logout' would restart the Window Manager. But, the same command changes nothing, even after a complete restart, the same problem recurs. 

My own session will run without issues. But, as soon as my daughter logs in to her account, she has the problem.

Please note, this is Xubuntu, so it's an xfce issue.

I can attach screen shots if that helps.

Any help appreciated. 

Art

---

### Post by DapperMe17 on 2011-12-01
Hit your ALT & F2 keys together...this should open a terminal run box. 

Type this... "xfwm4 --replace" (without the qoutes, of course), then hit the "run" button. 

Restart your PC and your in business!

:popcorn:

It's just a corrupt windows manager...which will be replaced with a new instance.

---

### Post by SkiyeSounds on 2011-12-01
that didnt work for me, was the first thing i tried. it was saving the corrupt session for some reason (even though attempts at not saving were made), and it wasnt allowing me to type in certain windows including the terminal unfortunately. if the above post is unsuccessful, this is how i solved - [http://ubuntuforums.org/showthread.php?t=1871376](http://ubuntuforums.org/showthread.php?t=1871376)

---

### Post by DapperMe17 on 2011-12-02
Before you try my instructions above, you can logout of your Xubuntu session, then login by using a "XFCE" session. 

You will have the same conflict, but this should at least allow you access the ALT/F2 run box....where you would type "xfwm4 --replace".

Once that's done, you can reboot, and select "Xubuntu" session at the login screen, to resume your desktop.

---

### Post by vangop on 2011-12-02
The decoration problems were caused for me by the logout action.
For some reason after pressing log out the system would wait for 10+ secs.
Upon next login I always had no decorations around the windows.
The fix is simple.
Log out. Ctrl+Alt+F1, login. 
```
 rm -rf .cache/sessions
```
Now get back to the graphical tty - ctrl+alt+F7 and login as usual.

---

### Post by SkiyeSounds on 2012-01-07
> **vangop said:**
> 
The fix is simple.
Log out. Ctrl+Alt+F1, login. 
```
 rm -rf .cache/sessions
```Now get back to the graphical tty - ctrl+alt+F7 and login as usual.
i had the same issue on a laptop, but ctrl+alt+f1 brought me to an endless loop of the computer not being able to find a sufficient display - i ran the above command in terminal with sudo privileges then restarted with the option to save session un-checked. when i logged back in, it worked perfectly.

---

### Post by LinuxFan999 on 2012-01-07
Which version of Xubuntu are you using?

---

