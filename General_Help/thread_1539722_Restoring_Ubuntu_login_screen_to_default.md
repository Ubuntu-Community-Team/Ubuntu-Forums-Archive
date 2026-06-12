---
title: "Restoring Ubuntu login screen to default"
date: 2010-07-26
forum: General Help
---

### Post by ksihawk7 on 2010-07-26
Recently I tried to change my login screen with plymouth in the terminal, i got to the part that shows all of the different login screens you can have, so I clicked the one I wanted. When I tried to log back in, the theme was basically the same as the default, but it made me click log in, enter my username, click accept again, then enter the password. So I was wondering how I could make it the default login screen where it's all on one screen.

---

### Post by BigCityCat on 2010-07-26
If you used the terminal then just hit the up arrow until you get the same command then I think the original is number 9.

---

### Post by josephellengar on 2010-07-26
What version of Ubuntu and gnome or kde?  I believe that they changed the GDM a lot between jaunty and karmic.  If you are using GDM you can do the following:

1) At GDM switch to tty1 with ctrl-alt-f1
2) log in textwise
3) enter: ```
 export DISPLAY=:0.0 
```
4) enter: ```
 sudo -u gdm gconf-editor 
```
5) go back to tty7
6) navigate to apps-GDM-simple-greeter.  One of those options might be what you want.

If you are trying to change the background or something you can always do steps 1-3 and for step 4 do ```
 sudo -u gdm gnome-control-center 
``` and step 4, then navigate to appearance.  You can change the background, theme, etc.  Hope this helped.

---

### Post by wojox on 2010-07-26
Did you look here [How do you change login and plymouth image in ubuntu 10.04 (Lucid Lynx)]("http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html")

---

