---
title: "Starting TeamViewer via Putty"
date: 2010-08-27
forum: General Help
---

### Post by CromagDK on 2010-08-27
It might be a totally different angle i should look at this, but here goes.

I can start the linux variant of teamviewer by writing teamviewer in the terminal, on the box. Fine.
I can start it via /opt/teamviewer/teamviewer/5/bin/teamviewer

If i connect to the box via ssh and putty, i still can run those commands but nothing happens.

My goal in this is to be able to start teamviewer remotely via putty.

Any thoughts ? :)

/Cromagdk

---

### Post by CromagDK on 2010-08-28
Bump

---

### Post by gradinaruvasile on 2010-08-28
I dont know if it will work. TeamViewer uses wine internally and i think it needs an x display to run on.

If you have putty access, you could use x11vnc (bound only to localhost) tunneled through ssh connection.

sudo x11vnc -localhost -display :0 -auth /var/lib/gdm/:0.Xauth  -xkb -forever

---

### Post by CromagDK on 2010-08-28
Thanks for your reply :)

But, will this start x11vnc server, or will this give me vnc access in putty ?
Dont think i understand.

/cromagdk

---

### Post by CromagDK on 2010-08-28
I'll try bump again.
Hope there are more suggestions out there ;)

/cromagdk

---

### Post by yajith on 2010-09-18
Try setting the DISPLAY variable and starting TeamViewer.

export DISPLAY=:0

Hope this helps.
cheers!

[http://yajith.blogspot.com/2010/09/teamviewer-stuff.html](http://yajith.blogspot.com/2010/09/teamviewer-stuff.html)

---

### Post by bodhi.zazen on 2010-09-18
No, that will not work. When you ssh into a box, with X forwarding, the default display is :10 , not :0 . Setting a DISPLAY will not work if X forwarding is not enabled.

First you will need an X server. If you are on Windows , use Xming.

When you connect, in Putty, allow X forwarding.

Tons of tutorials on a google search:

[http://www.math.umn.edu/systems_guide/putty_xwin32.html](http://www.math.umn.edu/systems_guide/putty_xwin32.html)

[http://solaris.reys.net/how-to-x11-forwarding-using-ssh-putty-and-xming/](http://solaris.reys.net/how-to-x11-forwarding-using-ssh-putty-and-xming/)

You may need to configure your ssh server to allow X forwarding, see the second link or ask the server admin for assistance.

---

### Post by yajith on 2010-09-18
@bodhi.zazen It does start the teamviewer application properly and allow remote connections, provided that you have saved login information ( remember password, sign in automatically etc. on teamviewer ) If not, X forwarding seems to be the way.

---

### Post by bodhi.zazen on 2010-09-18
> **yajith said:**
> @bodhi.zazen It does start the teamviewer application properly and allow remote connections, provided that you have saved login information ( remember password, sign in automatically etc. on teamviewer ) If not, X forwarding seems to be the way.

OK, I am unfamiliar with teamviewer.

---

### Post by yajith on 2010-09-18
@bodhi.zazen: It's just a convenient way of sharing the GUI login (Desktop?) In case password is not saved on to it, then X forwarding or a similar method has to be used to get it up as you said. :)

---

### Post by yajith on 2010-09-18
Update: Oops! Just checked it out and figured that the password saving part is not a must. :) Sorry! Just ignore that bit, it should even work without the saved log-in information.

---

### Post by sarmenhb on 2011-04-08
very simple i tried this on ubuntu 10.10.4 

do cd .. to go to root being /

then go into these directories

/opt/teamviewer/teamviewer/6/bin

ps i guess im running teamviewer 6 so thats i how i got to that dir so do ls in the second teamviewer folder and get in that version folder.

once in their you will see teamviewer in green as a executable

just type teamviewer and enter
nothing shows but it started.



ps: if your wondering how i found it (i was in ssh the whole time so no gui view)

type 
find / -name teamviewer  (in terminal)
and the last directores show the path where teamviewer is installed. so i tried it and it worked.

---

### Post by takitsan on 2011-04-08
yajith's method worked for me !!

If you have a saved-permanent password for teamviewer and you know the ID for the remote computer then connect via PuTTY and type:

```
export DISPLAY=:0
```and then
```
teamviewer
```this will run teamviewer on the remote machine and allow you to connect.  The terminal session will be locked as long as teamviewer is running.

If you want to keep using the terminal after starting teamviewer you can use &
```
teamviewer &
```this will start teamviewer, display the process ID and return to the terminal prompt.

Alternatively you can use 'screen'.  It allows multiple virtual terminals to be run.
If you don't have it install it by ```
sudo apt-get install screen
```you can then type ```
screen
```this will start a screen session i.e. a new terminal (at first use it displays an informational message.  Press Enter to proceed)

then you need to type the same commands as above```
export DISPLAY=:0
teamviewer
```and finally Ctr+a+d (keep Control pressed and then, without releasing Control, press 'a' and then 'd'.  This will bring you back to your initial terminal session.
If you want to return to the virtual teamviewer session type```
screen -dr
``` for more info on screen usage type ```
man screen
```Another method is to start a second session with PuTTY from the PuTTY menu.

Also, at least in my case, X forwarding was not necessary.

Using 10.10.

---

### Post by takitsan on 2011-05-03
Addendum.

For the above procedure to work, the user must be logged in (via the login screen, as tty) at the remote computer.

I managed to log in a tty user via ssh but couldn't get teamviewer to start.  Any ideas?

The remote screen can be locked (by Control+Alt+L for example).  Teamviewer will show the login screen and prompt you for the password.

---

### Post by takitsan on 2012-01-31
A crude method to login remotely is to:

edit [B]/etc/gdm/custom.conf
[/B]set **AutomaticLoginEnable=true **
and then reboot

---

