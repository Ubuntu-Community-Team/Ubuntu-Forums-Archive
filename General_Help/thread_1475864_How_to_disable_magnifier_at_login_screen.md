---
title: "How to disable magnifier at login screen ?"
date: 2010-05-07
forum: General Help
---

### Post by rostamiani on 2010-05-07
Si
I enabled Magnifier on ligin screen , then it didn't worked correctly and covered right half of my screen !
Now I cannot login and cannot disable magnifier and if I restart my computerT the magnifier will start again :mad:

How can I disable it ?

Thanks :lolflag:

---

### Post by rostamiani on 2010-05-07
My screen capture :

[IMG]http://www.iranimg.com/images/04374087460394739768.jpg[/IMG]

---

### Post by _0R10N on 2010-05-07
It looks like an Universal Accessibility  Preferences problem. You can take a look at that in the bar at the bottom of the login screen, or under your preferences menu.

---

### Post by rostamiani on 2010-05-07
> **_0R10N said:**
> It looks like an Universal Accessibility  Preferences problem. You can take a look at that in the bar at the bottom of the login screen, or under your preferences menu.
Thanks 
But I cannot login
I cannot see the right side of login screen to access magnifier options :D

---

### Post by piratebill on 2010-05-07
I am not sure exactly where those config files would be, but if you hit ctrl+alt+F2, you can log in through the terminal.  From there just rm the correct config files (you just have to find them first....)

---

### Post by _0R10N on 2010-05-08
> **rostamiani said:**
> Thanks 
But I cannot login
I cannot see the right side of login screen to access magnifier options :D

You can Ctrl+Alt+F1 to drop to a terminal. Then login and enter graphic mode. Then, as first step, go to System->Preferences->Assistive Technologies, and uncheck what is checked.

Kind regards!

---

### Post by rostamiani on 2010-05-08
I cannot enter the graphic mode !

When I use startx ,rwill recieve this error :

"Server is already active for display 0
if this server is no linger running, remove /tmp/.X0-lock"

But I cannot remove that file ,because I cannot login as root !
What's the root password ?I never set it before :D

---

### Post by _0R10N on 2010-05-08
> **rostamiani said:**
> I cannot enter the graphic mode !

When I use startx ,rwill recieve this error :

"Server is already active for display 0
if this server is no linger running, remove /tmp/.X0-lock"

But I cannot remove that file ,because I cannot login as root !
What's the root password ?I never set it before :D

You don't need to be root. If you're able to login into a terminal, then sudo rm the file
```
sudo rm /tmp/.X0-lock
``` 

Now that I see the name of the file, I'm flashing backward, I almost sure that I had this exactly same problem with debian 4...:-&

---

### Post by rostamiani on 2010-05-08
> **_0R10N said:**
> You don't need to be root. If you're able to login into a terminal, then sudo rm the file
```
sudo rm /tmp/.X0-lock
``` 

Now that I see the name of the file, I'm flashing backward, I almost sure that I had this exactly same problem with debian 4...:-&

Thanks , I'll try
Are you sure that sudo does not request the root password ? :p

---

### Post by rostamiani on 2010-05-08
Thanks a lot
I could remove the /tmp/.X0-lock

but now I cannot execute startx :D

This is the error :

> SocketCreateListener() failed
Make surean XServer isn't already running

What does it mean ?
Thanks

---

### Post by rostamiani on 2010-05-08
The problem solved
I used these commands :

> sudo service gdm stop
sudo X -configure

But I should do these steps before every logins !
all items at "System->Preferences->Assistive Technologies" are disabled !

---

### Post by rostamiani on 2010-05-09
Should I reinstall ubuntu ??? :(

---

### Post by waspinator on 2010-05-09
if you can log in using the terminal (ctrl+alt+f1), type in 

```
sudo apt-get remove --purge gnome-mag
```

That should fix it

EDIT. wrong command. try the corrected version. let me know if it works for you

---

### Post by rostamiani on 2010-05-09
> **waspinator said:**
> if you can log in using the terminal (ctrl+alt+f1), type in 

```
sudo apt-get remove --purge gdm-mag
```

That should fix it
Thanks a lot
I'll try now :D

---

### Post by rostamiani on 2010-05-09
It didn't work
This error occured :

E: Couldn't find package gdm-mag

---

### Post by waspinator on 2010-05-09
sorry I made a mistake. Try the corrected version. report back.

```
sudo apt-get remove --purge gnome-mag
```

---

### Post by rostamiani on 2010-05-10
> **waspinator said:**
> sorry I made a mistake. Try the corrected version. report back.

```
sudo apt-get remove --purge gnome-mag
```
Thanks a lot
The problem solved :D

---

### Post by LewtenantDan on 2010-07-09
Ok, so it's a simple fix.  It involves no code and no removal of any software.

The magnifier covers half of the screen, but it doesn't disable the half of the screen it is covering.  I had the same problem and after clicking in the dark along the taskbar for a little while, I was able to bring up the accessibility options dialogue box again and low and behold, screen magnifier was still checked.  The accessibility preferences button is about 1/6 of the way across the screen from the right edge.  Click on the taskbar in that area, then move the mouse just above the taskbar and to the left a bit and click again.  You should see the dialogue box pop up.  Uncheck the box and you're good to go :)  You may need to feel around in the dark a bit, but you'll get it as long as you bring the mouse up and left every time after you click on the taskbar.  Good luck, it worked for me!

EDIT::removing the gnome-mag software in recovery mode is an option, but if you ever reinstall it, it will automatically pop back up on the login screen, so taking 5-10 minutes to attack the source of the problem instead of just deleting it is probably your best bet.

---

### Post by warrencaldwell on 2010-09-03
> **LewtenantDan said:**
> Ok, so it's a simple fix.  It involves no code and no removal of any software.

The magnifier covers half of the screen, but it doesn't disable the half of the screen it is covering.  I had the same problem and after clicking in the dark along the taskbar for a little while, I was able to bring up the accessibility options dialogue box again and low and behold, screen magnifier was still checked.  The accessibility preferences button is about 1/6 of the way across the screen from the right edge.  Click on the taskbar in that area, then move the mouse just above the taskbar and to the left a bit and click again.  You should see the dialogue box pop up.  Uncheck the box and you're good to go :)  You may need to feel around in the dark a bit, but you'll get it as long as you bring the mouse up and left every time after you click on the taskbar.  Good luck, it worked for me!


This worked for me, thanks. The only addition I would make is that you don't have to 'feel around in the dark' to bring up the accessibility menu. On my screen I can still see the left half of the login dialog box on the unmagnified left half of the screen, and if you click slowly along the bottom right side of the screen, you can tell when you hit the accessibility button because the login dialog box un-highlights. Then, as LD says, click once more up and left (I got it first try) to bring up the options box. Worked like a charm.

---

### Post by andrewsomething on 2010-09-15
Here's a quick one liner that seems to work for me:

```
sudo -u gdm gconftool-2 /desktop/gnome/applications/at/screen_magnifier_enabled --type bool --set false
```

---

### Post by sreesha.c.n on 2011-04-24
Enter as root user in the terminal
cd to /usr/bin

execute: rm -r magnifier

---

