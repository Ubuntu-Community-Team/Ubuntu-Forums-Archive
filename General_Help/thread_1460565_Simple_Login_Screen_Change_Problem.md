---
title: "Simple Login Screen Change Problem"
date: 2010-04-23
forum: General Help
---

### Post by TurtleKing on 2010-04-23
I can't seem to be able to apply the simple GDM for the login screen. I can open the gnome-control-center/appearance. However, it will not let me install the GDM-LoginScanFusion.tar.gz file or any other them for that matter. 

I notice I can see all the files within the .tar.gz folder when i switch it to all files instead of theme package, but can't install them individually or the entire .tar.gz folder.

Please help this login screen looks awesome, and I would really love to see it when I startup my PC.

The login screen is called Login Scan 'fusion' in the following link:
[http://art.gnome.org/themes/gdm_greeter](http://art.gnome.org/themes/gdm_greeter)

---

### Post by devildoc5 on 2010-04-23
```
http://ubuntuforums.org/showthread.php?t=10223

http://ubuntuforums.org/showthread.php?t=919363&page=2

http://forumubuntusoftware.info/viewtopic.php?f=65&t=4124
```

google....

---

### Post by TurtleKing on 2010-04-23
Did you even read my post other than the subject? I don't have a problem getting from A to B, my problem is getting from B to C. I can't get the Appearance in GDM to recongnize the tar.gz file, so I can install it.:(

---

### Post by TurtleKing on 2010-04-23
bump

---

### Post by TurtleKing on 2010-04-24
2 bump

---

### Post by TurtleKing on 2010-04-24
Maybe this picture can "help someone help me" fix this problem.
[IMG]http://i277.photobucket.com/albums/kk59/Alexthesimba/Screenshot.png[/IMG]

Notes:
1. Notice the window on the right containing the GDM-LoginScreenTheme-tar.gz files.

2. Window on the left the error once I try to install it.

---

### Post by TurtleKing on 2010-04-24
bump

---

### Post by TurtleKing on 2010-04-25
Someone please help, I really don't want to have to update to Ubuntu 10 just to see this awesome theme.

---

### Post by TurtleKing on 2010-04-25
bump :(

---

### Post by TurtleKing on 2010-04-25
bump 2

---

### Post by TurtleKing on 2010-04-26
bump 3. I guess my only option is to wait for the Ubuntu 10 update.

---

### Post by conradin on 2010-04-26
Can you show us where you got this theme from?

---

### Post by P4man on 2010-04-26
You can keep bumping, but the answer was already given had you bothered to read the links. Or had you tried google

You are trying to install a gdm theme, you dont do that in system > preferences > appearances, you do that in system > adminstration > login screen for ubuntu <9.10. If you have >=9.10 you basically cant install a theme:
[http://ubuntuforums.org/showthread.php?t=1311284](http://ubuntuforums.org/showthread.php?t=1311284)

---

### Post by TurtleKing on 2010-04-26
> **conradin said:**
> Can you show us where you got this theme from?
This is where i got it from:
[http://art.gnome.org/themes/gdm_greeter]("http://art.gnome.org/themes/gdm_greeter")

[QUOTE=P4man]you do that in system > adminstration > login screen for ubuntu <9.10[/QUOTE]
I am going to copy this from first post since you skipped it which is understandable:

> I can open the gnome-control-center/appearance. However, it will not let me install the GDM-LoginScanFusion.tar.gz file or any other them for that matter.

I have tried already the google way (other post on this area) before posting here, thats how I learned to open GDM control-center-appearance (same thing as loginscreen GDMsetup from previous version although loginscreen setup does not have an install option only lets me choose from the packages installed). But as they say pictures are better than words:
1.Your suggestion even after I click on unlock and was asked for my password.
[IMG]http://i277.photobucket.com/albums/kk59/Alexthesimba/Screenshot-1.png[/IMG]
2. I tried to get a picture of the menu appearance, but since I have to do it from login *screen* it will not save the picture. Anyways I will post the link that I used to open the menu:

A.Post from where I got the method of opening the login screen:
[http://ubuntuforums.org/showthread.php?t=1294929]("http://ubuntuforums.org/showthread.php?t=1294929")

B. Instructions I followed that work, but will not let me install:
[http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html]("http://ubuntuforums.org/showthread.php?t=1294929")

By the way, did you think I just posted without checking out the links? I did my friend, but my problem is other area.

---

### Post by TurtleKing on 2010-04-26
bump

---

### Post by P4man on 2010-04-26
please read more carefully: Last time: the appearance menu, regardless if you access it from system > preferences > appearance or the way you do it through gnome-control-center > appearance - its the exact same thing- does NOT let you install GDM greeter themes.

 In fact; since ubuntu 9.10 nothing does. If you want to use that theme; install ubuntu 9.04 and use the loginscreen dialogue to install that theme. To customize 9.10 and 10.04 GDM greeters, see the links already given to you. But you cant use that theme.

---

### Post by TurtleKing on 2010-04-26
okay thank you, now I understand would have helped he would have said that the theme does not work rather than have me read the entire threads.

---

### Post by TurtleKing on 2010-04-26
Well looks like your only able to change the background picture to whatever you want it to be for the loginscreen, cannot change the icons to something else other than the color of it on my PC. So I guess that will do for me till next update is released, should I mark this as solved or let it die out?

---

### Post by P4man on 2010-04-26
You can change icons, and background and font, though its a bit of a hack. Did you see this:
[http://ubuntuforums.org/showpost.php?p=8271948&postcount=10](http://ubuntuforums.org/showpost.php?p=8271948&postcount=10)

BTW, 10.04 has the same greeter and the same lack of theming for it.

---

### Post by towheedm on 2010-04-26
> **TurtleKing said:**
> Well looks like your only able to change the background picture to whatever you want it to be for the loginscreen, cannot change the icons to something else other than the color of it on my PC. So I guess that will do for me till next update is released, should I mark this as solved or let it die out?


Despite popular beliefs, GDM is highly customizable.  The only thing that's almost impossible to change is the simple greeter, and I stress ALMOST impossible.  And that's only because it requires a great deal of knowledge in UI design.  Probable easier for programmers than themers.

Check out the link at the beginning of this thread:
[http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

It should prove useful to customizing GDM.

---

### Post by mcoleman44 on 2010-04-26
A GDM theme cannot be installed that way. And you cant install GDM themes anywhere if your using 9.10

---

### Post by towheedm on 2010-04-26
The GDM is Karmic cannot be themed in the true sense of the work, but again despite popular beliefs, it IS highly customizable.  Repeat CUSTOMIZABLE.

---

