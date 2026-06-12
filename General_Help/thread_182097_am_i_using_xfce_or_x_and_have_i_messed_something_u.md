---
title: "am i using xfce or x? and have i messed something up?"
date: 2006-05-25
forum: General Help
---

### Post by bobdazzla on 2006-05-25
Hi there,

I'm completely new this linux thing, please bear with me. 

I wanted to get my Kubuntu 5.10 system to auto-login, so that I could run it as a headless, keyboardless server. I searched the ubuntu furoms and came across this post:

[http://www.ubuntuforums.org/showthread.php?t=152274](http://www.ubuntuforums.org/showthread.php?t=152274)

and followed it step-by-step. After completing the final step, of removing all the login managers, it suddenly occured to me that this might have been a bad idea! Are there significant enough differences between ubuntu and kubuntu such that this guide won't work? and I haven't tried rebooting the system yet (waiting for approval here first!), but would doing so lock me out?

Assuming that guide IS effective on Kubuntu... am I running X or XFCE? This is a default Kubuntu install, but I'm really not sure. One of the steps of that guide differs depending on which one you are using, so I need to be sure of this.

Thanks in advance

---

### Post by Fass on 2006-05-25
[XFCE](http://www.xfce.org/) is a desktop environment, like [Gnome](http://www.gnome.org/) and [KDE](http://www.kde.org/). If you're running Kubuntu and have not installed XFCE, you aren't running XFCE.

[X](http://en.wikipedia.org/wiki/X_Window_System) (in Ubuntu's case X.org) is a window system - it is what Gnome, KDE and XFCE "run on." Everyone who has a graphical environment in Ubuntu has some version of X.

Those instructions will not work if you don't have XFCE, in that there is no XFCE to start. If you skip everything after "let's make the autostart:" line, it will apparently log you on without any sort of X or desktop environment running.

---

### Post by Monster_user on 2006-05-25
I am not sure of the differences between XFCE (Xubuntu), and KDE (Kubuntu). However, I think if you change the .bash_profile, then it should work with Kubuntu.

> his will make the autologin stuff...

let's make the autostart:

Code:
```
nano .bash_profile
```

put this code on the bottom and save it

```

 if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then 
           startkde 
 fi

```



That should set it to start KDE.

[Gnome - Ubuntu 6.06](http://shots.osdir.com/slideshows/slideshow.php?release=630&slide=4&title=ubuntu+6.06+flight+7+screenshots)

[KDE - Kubuntu 6.06](http://shots.osdir.com/slideshows/slideshow.php?release=631&slide=4&title=kubuntu+6.06+flight+7+screenshots)

[XFCE -Xubuntu](http://shots.osdir.com/slideshows/slideshow.php?release=632&slide=4&title=xubuntu+6.06+flight+7+screenshots)

---

### Post by bobdazzla on 2006-05-25
Thank you for the clarification fass, im not sure what led me to think I was using xfce in the first place, but fortunately i haven't rebooted yet so I can go back and undo all those changes I made.

Monster_user, I think I'm going to try your advice...

thanks again

---

### Post by Video Toaster on 2006-05-25
[QUOTE=bobdazzla]Hi there,

I'm completely new this linux thing, please bear with me. 

I wanted to get my Kubuntu 5.10 system to auto-login, so that I could run it as a headless, keyboardless server. I searched the ubuntu furoms and came across this post:

[http://www.ubuntuforums.org/showthread.php?t=152274](http://www.ubuntuforums.org/showthread.php?t=152274)

and followed it step-by-step. After completing the final step, of removing all the login managers, it suddenly occured to me that this might have been a bad idea! Are there significant enough differences between ubuntu and kubuntu such that this guide won't work? and I haven't tried rebooting the system yet (waiting for approval here first!), but would doing so lock me out?

Assuming that guide IS effective on Kubuntu... am I running X or XFCE? This is a default Kubuntu install, but I'm really not sure. One of the steps of that guide differs depending on which one you are using, so I need to be sure of this.

Thanks in advance[/QUOTE]
If you want to run a server, is there any reason you need to be logged on *at all* when not maintaining the server?  I have an Ubuntu box running Samba and I just leave it on the logon screen when I'm not maintaining it.

Anyways, I'm pretty sure you can just leave your logon setup the way it was originally and just leave the machine logged off.

---

### Post by bobdazzla on 2006-05-25
video toaster,

my logic here is that, while i am familiar with the cli, i still feel "safer" doing config stuff with a gui. And as far as i know (and granted i don't know a lot), it would be easier for me to have my system configured to, upon boot, autologon to kubuntu and then automatically run the built-in VNC server at startup, and configure that to "always listen" for VNC requests. That way if I ever need to change anything on the kubuntu server (which again is headless, keyboardless, and basically it would be a pain in the butt to haul it out of my hall closet so i could hook those things up), I could just use the VNC client on my windows xp machine and then have the nice pretty gui waiting there for me.

someday, i hope to be versed into the dark linux arts enough as to where i could stay logged off and just do all changes over vnc through the cli, but till then i think the above plan would be my best bet... but if you have any suggestions though i'd like to hear them.

---

### Post by Video Toaster on 2006-05-25
[QUOTE=bobdazzla]video toaster,

my logic here is that, while i am familiar with the cli, i still feel "safer" doing config stuff with a gui. And as far as i know (and granted i don't know a lot), it would be easier for me to have my system configured to, upon boot, autologon to kubuntu and then automatically run the built-in VNC server at startup, and configure that to "always listen" for VNC requests. That way if I ever need to change anything on the kubuntu server (which again is headless, keyboardless, and basically it would be a pain in the butt to haul it out of my hall closet so i could hook those things up), I could just use the VNC client on my windows xp machine and then have the nice pretty gui waiting there for me.

someday, i hope to be versed into the dark linux arts enough as to where i could stay logged off and just do all changes over vnc through the cli, but till then i think the above plan would be my best bet... but if you have any suggestions though i'd like to hear them.[/QUOTE]
Oh, OK!  VNC server!  Yeah, I'm pretty sure you need to be logged on for that, so your solution makes sense.

Don't get rid of KDM.  Open up System Settings and click Login Manager.  After clicking "Administrator Mode" and entering your password, click the Convenience tab.  You can enable auto-logon from there.

Hope that helps!

---

### Post by bobdazzla on 2006-05-25
[QUOTE=Video Toaster]
Don't get rid of KDM. 
[/QUOTE]

Too late! :(

can you save me about two hours of frustrated googling and tell me how to get it back? would it just be something like 

apt-get install KDM

?

edit:

evidentally the "sudo apt-get remove KDM" (which i did as per the instructions in the linked HOWTO) did not remove KDM after all; user profiles was still there, i ticked "autologon" next to my username, and all is well.

thanks again for everyones help

---

### Post by Monster_user on 2006-05-26
[QUOTE=bobdazzla]evidentally the "**sudo apt-get remove _KDM_**" (which i did as per the instructions in the linked HOWTO) did not remove KDM after all...[/QUOTE]

Linux is case-sensitive. Most everything is in lower case.

'KDM', 'kdm', and 'Kdm' are three different things.  So that would be where your luck came into play.

---

