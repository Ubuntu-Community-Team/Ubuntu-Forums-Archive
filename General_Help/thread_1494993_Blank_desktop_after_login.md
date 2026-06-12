---
title: "Blank desktop after login"
date: 2010-05-27
forum: General Help
---

### Post by Kid A on 2010-05-27
The title says it all, after I log in I have the desktop background and the cursor but nothing else.  I was poking around in some text files trying to get synergy to work properly..I think maybe I broke something.

Running ubuntu 10.04, Radeon xpress 200.  I've tried failsafe mode and no dice.

thanks in advance.

---

### Post by wojox on 2010-05-27
When you get to your minimal desktop.

Press Alt+F2 and type **gnome-terminal**

enter:

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
``` 

```
sudo reboot
```

---

### Post by Kid A on 2010-05-27
when i type "gnome-terminal" it returns with:  Failed to parse arguments: Cannot open display

reinstalling the gnome desktop environment again to see if that does it...

---

### Post by Kid A on 2010-05-28
This is really astounding (i think there are super natural forces prohibiting me from getting synergy to work properly);  I have synergy enabled to work with ubuntu before the login screen comes up.  However whenever I have the necessary code in there to make that possible, my desktop hangs.  I get the background with nothing but a mouse cursor.  Here is all the editing that I did:

/etc/gdm/Init/Default
```
/usr/bin/killall synergys
while [ $(pgrep -x synergys) ]; do sleep 0.1; done
/usr/bin/synergys
```/etc/gdm/PostLogin/Default

```
 /usr/bin/killall synergys
while [ $(pgrep -x synergys) ]; do sleep 0.1; done 
```made an executable:  sudo chmod +x /etc/gdm/PostLogin/Default 

/etc/X11/Xsession.d/85synergys

```
 /usr/bin/killall synergys
while [ $(pgrep -x synergys) ]; do sleep 0.1; done
/usr/bin/synergys  
```made an executable:
sudo chmod +x /etc/X11/Xsession.d/85synergys

---

### Post by Kid A on 2010-05-28
please ignore me, i'm a total idiot.  i forgot to make one of the files and executable, so synergy wasn't getting killed after login.  everything's working now :redface:

---

