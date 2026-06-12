---
title: "HAL Daemon Is not running"
date: 2010-02-14
forum: General Help
---

### Post by crowds0 on 2010-02-14
I'm running Xubuntu 9.10. At the login prompt, I get the error message 'Xfce power manager HAL daemon is not running'  then I can't login for about 10 seconds.  This problem seemed to arise after trying to load a CD over USB in Rhythmbox, but that may have nothing to do with it.

sudo start hal

says the job is already running.  I found someone with the same issue here: [http://ubuntuforums.org/showthread.php?t=728343](http://ubuntuforums.org/showthread.php?t=728343)

And it's marked as 'solved' but the solution was to move to KDE, which i'd rather not real with.  Any suggestions?

---

### Post by rcayea on 2010-02-14
If you look in /etc/X11/xorg.conf file it should be listed on the last line for daemons. This is where mine are listed anyway. 

you can access this line by typing:

sudo gedit /etc/X11/xorg.conf

---

### Post by rcayea on 2010-02-14
Or, if you have Ubuntu-Tweak installed, you can add it to the list of startup apps using that software.

---

### Post by crowds0 on 2010-02-14
Thanks for the reply.  I don't seem to have a xorg.conf file.  Are you running 9.10?  I think that there's a new method for configuring the X server now, but i'm not sure what it is.  Also, in my 'Session and Startup' I have the 'XFCE power manager' checked to begin on startup.  And the HAL daemon (hald) does seem to be running when I do a 'ps'  I just don't know why it gives me the error and then freezes before I login.

---

### Post by Twiggeh on 2010-03-17
I have exactly the same problem, running Xubuntu 9.10 on my laptop, and when i log in xfce power manager gives me a popup-error about hal daemon not running and i cant move my mouse for a few seconds.
[http://img219.imageshack.us/img219/5223/screenshotgt.png](http://img219.imageshack.us/img219/5223/screenshotgt.png)

And if i do a sudo service hal start it gives me :
"start: Job is already running: hal"

This is starting to be quite annoying..

---

### Post by crowds0 on 2010-03-18
> **Twiggeh said:**
> I have exactly the same problem, running Xubuntu 9.10 on my laptop, and when i log in xfce power manager gives me a popup-error about hal daemon not running and i cant move my mouse for a few seconds.
[http://img219.imageshack.us/img219/5223/screenshotgt.png](http://img219.imageshack.us/img219/5223/screenshotgt.png)

And if i do a sudo service hal start it gives me :
"start: Job is already running: hal"

This is starting to be quite annoying..

So this is the same problem I had and I don't recall what exactly I did.  It may have been an apt-get upgrade, or I may have not have been selecting the "Xfce Power Manager" in the startup applications in "Sessions and Startup" in the "Settings Manager."
Try that, or I would also suggest making a new account and see if you still have the same issue.

---

### Post by kjtruitt on 2010-03-19
Probably not the same issue but I got a message about Hal daemon not running and was *unable* to complete boot up.  I have a 10-year-old laptop and hard drive and I selected ext4 during configuration.  It worked when I selected ext3.

---

### Post by athelas on 2010-03-21
Hi.
I've got the same message and I found a good suggestion in the german ubuntuusers forum.
It looks like the problem mainly occurs, when you have a cd or a dvd in your drive, while you start Linux.
So I took the CD out of my drive and it worked again.

---

### Post by blg on 2010-03-22
> **rcayea said:**
> If you look in /etc/X11/xorg.conf file it should be listed on the last line for daemons. This is where mine are listed anyway. 

you can access this line by typing:

sudo gedit /etc/X11/xorg.conf

This is not correct. /etc/X11/xorg.conf should not have anything in it except xorg configuration settings.  

You may be thinking of /etc/X11/Xsession or /etc/X11/xinit/xinitrc


I too am getting the "HAL Daemon Is not running" error on startup and can confirm that it is repeatable.  Put a CD in my drive and reboot, got error.  Remove CD, reboot, no error.  

One reboot with error, I logged into a console with <ctrl><alt><F1>, and ran:
ps ax |grep hald

to confirm that the HAL Daemon was in fact running, regardless of this error message.

There must be some sort of bug in XFCE Power Manager.


Looks like it may have been fixed recently:
[https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/507097](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/507097)

---

