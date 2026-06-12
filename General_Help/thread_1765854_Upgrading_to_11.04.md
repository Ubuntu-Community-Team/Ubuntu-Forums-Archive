---
title: "Upgrading to 11.04"
date: 2011-05-23
forum: General Help
---

### Post by ddjolley on 2011-05-23
I recently moved from Fedora 9 to Ubuntu 11.04.  A few days ago I posted to this forum a problem that I was having.  That problem was/is that after logging in the screen goes blank momentarily and when it returns sometimes (not always) the cursor is missing.  I never received any responses to that post.

In trying to solve this problem, I noticed something that I believe to be unusual.  My 11.04 diaplay looks very much like the display that I'm used to seeing in 10.04.  My understanding is that the Unity interface of 11.04 is supposed to have a task bar down the left hand side.  I'm not seeing it.  It sure looks to me like I'm running the old interface.  Is that possible?  What should I do?  Maybe if I can get this fixed my cursor issues will also be cured.

Thanks for any input.

           ... doug

---

### Post by silkworm2.5 on 2011-05-23
I dont know how to fix the mouse error. But The interface error, maybe. At the login screen, there should be a dropdown box for selecting the interface you log into. If it says "Classic Ubuntu" you are using the old interface. If you see "Unity" then you are using the new one
 The bar at the side stays hidden when windows cross its path. Try moving the cursor up to the top left of the screen to unhide it if you are in Unity.

---

### Post by ddjolley on 2011-05-23
> The bar at the side stays hidden when windows cross its path.
> Try moving  the cursor up to the top left of the screen to unhide it if you are in  Unity.

I don't see ANYTHING like that on the login screen.  I'm thinking I'm not in Unity.  Suggestions?

Thanks.

          ... doug

---

### Post by linuxinstalledfromhdd on 2011-05-23
Try doing a check on your video adapters and drivers and see if they are installed or not.

---

### Post by eltonw on 2011-05-23
> **ddjolley said:**
> > The bar at the side stays hidden when windows cross its path.
> Try moving  the cursor up to the top left of the screen to unhide it if you are in  Unity.

I don't see ANYTHING like that on the login screen.  I'm thinking I'm not in Unity.  Suggestions?

Thanks.

          ... doug

Go to System =Themes and Tweaks = Login Screen settings (you will need to provide your superuser / root password to unlock it. 
The last dialog line is Select [Ubuntu Classic] as default session.
Click on the dialog box.
This will present you with the following choices:

User Defined Session
Ubuntu (Safe Mode)
Ubuntu Classic (No Effects)
[COLOR="DarkOliveGreen"]**Ubuntu**[/COLOR] [...provides the Unity interface, select THIS one].
Ubuntu Classic
Recovery Console.

click on "Close" then reboot.

---

### Post by wildmanne39 on 2011-05-23
> **ddjolley said:**
> I recently moved from Fedora 9 to Ubuntu 11.04.  A few days ago I posted to this forum a problem that I was having.  That problem was/is that after logging in the screen goes blank momentarily and when it returns sometimes (not always) the cursor is missing.  I never received any responses to that post.

In trying to solve this problem, I noticed something that I believe to be unusual.  My 11.04 diaplay looks very much like the display that I'm used to seeing in 10.04.  My understanding is that the Unity interface of 11.04 is supposed to have a task bar down the left hand side.  I'm not seeing it.  It sure looks to me like I'm running the old interface.  Is that possible?  What should I do?  Maybe if I can get this fixed my cursor issues will also be cured.

Thanks for any input.

           ... dougHi, if you do it from the log in screen you have to click on your user name then look at the bottom of the screen, and it will say ubuntu that is the one for unity, it does not actually say unity, but if you can not run unity you might be able to go to administration then click on additional drivers and enable the driver for your video card, then restart the computer.:D

---

### Post by ddjolley on 2011-05-24
> if you do it from the log in screen you have to click on your user  name
> then look at the bottom of the screen, and it will say ubuntu that  is the
> one for unity, it does not actually say unity, but if you can not  run unity
> you might be able to go to administration then click on  additional drivers
> and enable the driver for your video card, then  restart the computer.

Viola!  I got Unity running as evidenced by the presence of the task bar down the left hand side.  Thanks a batch.

FWIW, I noticed that when I clicked on the user name and then Ubuntu (before I installed the drivers) I would boot in "classic" mode; but, the occurrences of the missing cursor were drastically reduced.  IOW, it appears that clicking on 'Ubuntu' goes a long way towards fixing the missing cursor problem in classic mode.  When I click on 'Ubuntu' I almost never get a missing cursor.  Without clicking on Ubuntu I almost always get the missing cursor.  Of course once the proper drivers are installed, I'm in Unity and all of these issues seem to melt away.

Thanks to all for the help.

              ... doug

---

