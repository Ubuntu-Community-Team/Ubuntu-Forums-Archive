---
title: "No System Tray Detected On This System"
date: 2010-03-18
forum: General Help
---

### Post by cdo on 2010-03-18
Somewhere along the line while trying to reset the Ubuntu panels i lost the system tray getting the message in the title . Now , when i log on and get to the desktop i have no way to get anywhere else .

Managed to get on - line via Help icon on log off screen . Is there any way for me to get these functions back without re - installing from scratch ?

---

### Post by qwerty2009 on 2010-03-18
right click your panel and select add to panel

scroll down and add the notification area applet to the panel

---

### Post by cdo on 2010-03-18
That won't work as there are no Linux panels to right click on . If i hit alt . space i just go back to Help entry point and screen greys out .

---

### Post by ninjamaster945 on 2010-03-18
So you don't have any panels? Try pressing alt + F2, then enter "gnome-panel" (without quotes), and click run. Let me know if that fixes your problem

---

### Post by cdo on 2010-03-18
Tried but function would not respond .

---

### Post by cdo on 2010-03-18
Does anyone know a method that will allow me to get into file system or home folder in order to back up data to a cd when i have no panels displaying and system tray is not detected ?

---

### Post by ManyuX95 on 2010-03-18
make alt+f2 and: "nautilus --no-desktop computer:" without quotes

---

### Post by ubu newb on 2010-03-18
Not sure if this is the same problem but I lost my panels a couple of weeks ago.  Tempboss gave me the following solution and I got them back.   As I said, not sure if it's the same but may not hurt to try:

It seems like your panels are just gone. What I'd like you to do is  press Ctrl+Alt+F1. This will take you to a black screen and let you  login. It won't show your password as you type it, but it's still  putting in your password. Then it will give you the command line. I'd  like you to type in this command:

```
rm -rf .gconf .gnome .gnome2
```Ideally it will give you no  reply back, it will just give you the prompt again. Then restart Ubuntu  by doing this command:

```
sudo shutdown -r now
```See if that brings up your panels when  it restarts.

---

### Post by ManyuX95 on 2010-03-18
Hey! If you fixed the problem then tell us :D, maybe my help was not the best but that is what we are here for, to learn

---

### Post by showgun22 on 2010-04-26
I was having the same problem 
I use your command line and I am back in business.
It works fine
Thanks

---

