---
title: "Multi Session login with vnc?"
date: 2009-12-18
forum: General Help
---

### Post by prettyhatem on 2009-12-18
Hey I am pretty new with linux and ubuntu.  But I decided to create a fileserver/media center machine for my living room.  So far it has been a fantastic experience that I wouldn't be able to do without the search function on these forums!

But now I want to do something that I am not sure is possible.

I have my machine hooked up to a TV via DVI.  On that screen I have it logged into a user and it is running XBMC.

What I would like to do is be able to VNC into that same computer and log into another user in gnome.  So I can see the desktop and such with out effecting the screen that is currently hooked up to the DVI.  So basicly have to desktop "sessions" running at once and one being connected to DVI while the other is just connected via VNC.

It is Ubuntu 9.10 and I am using x11vnc for my vnc viewer right now because of the compiz issue with my nvidia drivers.

I have searched and searched and have yet to find an answer to this....

thanks!

---

### Post by krunge on 2009-12-18
By default x11vnc will connect to the X display on the physical graphics hardware.  So you probably want the "vncserver" package instead (virtual desktop sessions.)

BTW, if you install the "xvfb" package and then use "x11vnc -create" it can create virtual (i.e. RAM-only) desktops as well.  If you go that route, ask if you have any questions.

---

### Post by prettyhatem on 2009-12-18
wow that sounds easy, will it conflict with my current x11vnc service running if I install "xvfb"?

I installed x11vnc using this guide, [http://ubuntuforums.org/showthread.php?t=45565](http://ubuntuforums.org/showthread.php?t=45565)

---

### Post by prettyhatem on 2009-12-18
Also I should note a couple things, I want to be able to keep he "virtual gnome session" logged in even if I close my VNC connection.  I am testing this all out on in a VM before I commit anything to my fileserver..

It is possible to have two "gnome" desktops running though correct?  I tried the vncserver just now and it vnc'd into a very slim black and white windows thingy....

---

### Post by prettyhatem on 2009-12-18
Last question, Will I be able to still VNC into the original physically connected desktop?

---

### Post by krunge on 2009-12-18
> **prettyhatem said:**
> wow that sounds easy, will it conflict with my current x11vnc service running if I install "xvfb"?

No, the Xvfb program will not be set up as a service.  It will just be a program sitting on your hard disk waiting for other programs (i.e. x11vnc -create) to run it.
> I installed x11vnc using this guide,
[http://ubuntuforums.org/showthread.php?t=45565](http://ubuntuforums.org/showthread.php?t=45565)
No, it won't conflict with that.  I assume you understand that TCP ports 5900, 5901, 5902, ... etc are used by the VNC servers, so, if you run multiple ones at the same time, you will have to deal with knowing which port belongs to which VNC server (your above link tries to inform you which port is being used by x11vnc.)

---

### Post by krunge on 2009-12-18
> Also I should note a couple things, I want to be able to keep the "virtual gnome session" logged in even if I close my VNC connection.

Yes, that will work.
> 
It is possible to have two "gnome" desktops running though correct?

Yes, as many as you want.  One important note though: the "x11vnc -create" mechanism will first try to FIND any existing desktop session you have, and connect to that instead of creating a new one.  This "finding" applies to both the desktop session on the physical h/w or a virtual one (x11vnc can't really tell the difference.)

So to have multiple virtual gnome desktops all with the same user you could run multiple commands like this:
```

x11vnc -create -env FD_TAG=my_gnome_1 -env FD_SESS=gnome -rfbport 5901
x11vnc -create -env FD_TAG=my_gnome_2 -env FD_SESS=gnome -rfbport 5902

```
Well, there are fancier, cleaner ways to have multiple ones for the same user, but I hold off those details for now to avoid confusion.
> I tried the vncserver just now and it vnc'd into a very slim black and white windows thingy....
Yes, I think you need to edit ~/.vnc/xstartup and put in the "gnome-session" command for the window manager instead of the default they put in there.
> 
Last question, Will I be able to still VNC into the original physically connected desktop?

Yes. An -rfbport example like the above would work (replacing "-create" with "-display :0") but as I say there are fancier ways to manage this.

---

### Post by prettyhatem on 2009-12-18
Wow fantastic info! thanks soooo much.  Though I am running into some more newbie issues.

I do have vnc currently setup with the port 5900 being connected to the current display.  So if I just want to create an additional session, I would do this?

x11vnc -display :0 -env FD_TAG=my_gnome_1 -env FD_SESS=gnome -rfbport 5900
x11vnc -create -env FD_TAG=my_gnome_2 -env FD_SESS=gnome -rfbport 5901

Would I put these commands in "/usr/local/bin/sharex11vnc"?

I really appreciate your help!

---

### Post by prettyhatem on 2009-12-18
Also, there doesnt appear to be a ~/.vnc/xstartup file.  There is if I make a vncserver -create, but now if I do the x11vnc -create that you specified.  

When I try x11vnc -create -env FD_TAG=my_gnome_1 -env FD_SESS=gnome -rfbport 5901 it says "Listening for VNC connections on TCP port 5901" but when I attempt to connect to port 5901 

```
18/12/2009 15:18:09 Got connection from client 10.118.204.108
18/12/2009 15:18:09   other clients:
18/12/2009 15:18:09 wait_for_client: got client
18/12/2009 15:18:09 wait_for_client: running: env X11VNC_SKIP_DISPLAY='' /bin/sh /tmp/x11vnc-find_display.bDYKgj
18/12/2009 15:18:09 wait_for_client: find display cmd failed
18/12/2009 15:18:09 wait_for_client: FINDCREATEDISPLAY cmd: /bin/sh /tmp/x11vnc-find_display.bDYKgj Xvfb
trying N=20 ...
18/12/2009 15:18:10 wait_for_client: read failed: /bin/sh /tmp/x11vnc-find_display.bDYKgj Xvfb
18/12/2009 15:18:10 fgets: Bad file descriptor
```

And closes the connection.

---

### Post by krunge on 2009-12-18
> 
I do have vnc currently setup with the port 5900 being connected to the current display.  So if I just want to create an additional session, I would do this?

That's a good question.  I'm worried that you might have vino running during some of your tests and not know it and that might cause confusion.  So I am tempted to have you use ports 5901 and 5902 for x11vnc to avoid any collisions with vino (or anything else) on port 5900

BTW your firewall (if one is running) will need to allow incoming connections to all of these ports (nowadays this seems to happen automatically, but I mention it just in case.)

I don't think your "/usr/local/bin/sharex11vnc" startup script method will work well here because *both* X desktop sessions would run it.  Is that scheme working well for you to access the physical display :0 ?  If so maybe I can think of a way to still use it for :0 and something else for your "virtual" one.

I suggest getting things working one at a time and then trying to put them together.

---

### Post by krunge on 2009-12-18
> **prettyhatem said:**
> Also, there doesnt appear to be a ~/.vnc/xstartup file.  There is if I make a vncserver -create

Yes, I think you need to run vncserver once to have it make it (BTW, vncserver doesn't have a -create option)

So if you now have a "xstartup" file made by vncserver, if it has a line in there that runs "twm" or some other lightweight window manager, you should change that line to run "gnome-session".
> 
but now if I do the x11vnc -create that you specified.  

When I try x11vnc -create -env FD_TAG=my_gnome_1 -env FD_SESS=gnome -rfbport 5901 it says "Listening for VNC connections on TCP port 5901" but when I attempt to connect to port 5901 

```

...
18/12/2009 15:18:09 wait_for_client: FINDCREATEDISPLAY cmd: /bin/sh /tmp/x11vnc-find_display.bDYKgj Xvfb
trying N=20 ...
18/12/2009 15:18:10 wait_for_client: read failed: /bin/sh /tmp/x11vnc-find_display.bDYKgj Xvfb
18/12/2009 15:18:10 fgets: Bad file descriptor
```

That doesn't look good.  Did you install the xvfb package?

---

### Post by prettyhatem on 2009-12-19
> **krunge said:**
> That's a good question.  I'm worried that you might have vino running during some of your tests and not know it and that might cause confusion.  So I am tempted to have you use ports 5901 and 5902 for x11vnc to avoid any collisions with vino (or anything else) on port 5900

BTW your firewall (if one is running) will need to allow incoming connections to all of these ports (nowadays this seems to happen automatically, but I mention it just in case.)

I don't think your "/usr/local/bin/sharex11vnc" startup script method will work well here because *both* X desktop sessions would run it.  Is that scheme working well for you to access the physical display :0 ?  If so maybe I can think of a way to still use it for :0 and something else for your "virtual" one.

I suggest getting things working one at a time and then trying to put them together.

Alright I will try on ports 5901 and 5902.

Dont have a firewall setup.

It doesnt really matter if we use the "/usr/local/bin/sharex11vnc" script, it works with display:0 right now, but I am only using it because that guide I linked to suggested it.

---

### Post by prettyhatem on 2009-12-19
> **krunge said:**
> Yes, I think you need to run vncserver once to have it make it (BTW, vncserver doesn't have a -create option)

So if you now have a "xstartup" file made by vncserver, if it has a line in there that runs "twm" or some other lightweight window manager, you should change that line to run "gnome-session".

That doesn't look good.  Did you install the xvfb package?

I have not installed the xvfb package.  Should I have?

just a quick note: I opted to install vnc4server from the Synaptic Package Manager.  I do see another choice, tightvncserver...

---

### Post by krunge on 2009-12-19
> I have not installed the xvfb package.  Should I have?

just a quick note: I opted to install vnc4server from the Synaptic Package Manager.  I do see another choice, tightvncserver...
Yes, for "x11vnc -create" mode the xvfb package (/usr/bin/Xvfb program) is needed.

But before you do that (as much as I'd like you to use "x11vnc -create" !!!), the vncserver route may be simpler for you since you say you don't have much unix experience.

I don't think there will be much difference between vnc4server and tightvncserver.  Both provide the "vncserver" command I believe.

So run something like:```
vncserver :5
``` This should start up a virtual X session (with a bare-bones window manager) for you that is accessible via a VNC viewer on vnc display 5, i.e. vnc port 5905.  I think you said you did something like this already.

This should create a file for you ~/.vnc/xstartup looking something like this:
```

#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
twm &

```
With a text editor, change that "twm" to "gnome-session".  Then kill and restart vncserver:
```

vncserver -kill :5
vncserver :5

```
This should give you a virtual X session, with gnome window manager, accessible on VNC port 5905 (e.g. "vncviewer host:5" from another computer)

Let's see how that goes.

---

### Post by prettyhatem on 2009-12-19
Alright, I did everything just mentioned and it worked!

I did install vnc4server.  I still havent installed xvfb.  Is there a benefit to using xvfb over just vncserver?

now that I ran vncserver :5 and it worked perfectly is that it?  Do I just create a script to make sure it has vncserver :5 after restart?

---

### Post by krunge on 2009-12-19
> 
It doesnt really matter if we use the "/usr/local/bin/sharex11vnc" script, it works with display:0 right now, but I am only using it because that guide I linked to suggested it.
For your display :0 access we might just modify that script to only do its x11vnc stuff if DISPLAY is :0, e.g.:
```

#!/bin/sh

if echo $DISPLAY | grep :0; then

    x11vnc -nap -bg -forever -rfbauth ~/.vnc/passwd -desktop "VNC${USER}@${HOSTNAME}"|grep -Eo "[0-9]{4}">~/.vnc/port.txt

    zenity --info --text="Your VNC port is `cat ~/.vnc/port.txt`"
fi

```
That way when your vncserver gnome-session runs, it will have a $DISPLAY of  :5 (see my earlier post) and will by-pass the x11vnc starting stuff.

---

### Post by krunge on 2009-12-19
> Alright, I did everything just mentioned and it worked!

Good!
> 
I did install vnc4server.  I still havent installed xvfb.  Is there a benefit to using xvfb over just vncserver?

I don't think so; however, it might depend on the questions or features you next ask for (if any.)
> 
now that I ran vncserver :5 and it worked perfectly is that it?  Do I just create a script to make sure it has vncserver :5 after restart?
You mean so "vncserver :5" is run when the machine reboots?  Or something else?  A crontab might be a good way to start it at boottime.

---

### Post by prettyhatem on 2009-12-19
> **krunge said:**
> 
You mean so "vncserver :5" is run when the machine reboots?  Or something else?  A crontab might be a good way to start it at boottime.

Sorry, I mean will this new session be able to connect if I just reboot the server?  with vncserver know to run a session on :5 automatically?

Also I noticed when I logged into the :5 I got an error window stating 


"An Error occurred while loading or saving configuration information for evolution-alarm-notify. Some of your configuration settings may not work properly.

Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-nYrKIbHNjI: Connection refused)"

---

### Post by prettyhatem on 2009-12-19
> **krunge said:**
> For your display :0 access we might just modify that script to only do its x11vnc stuff if DISPLAY is :0, e.g.:
```

#!/bin/sh

if echo $DISPLAY | grep :0; then

    x11vnc -nap -bg -forever -rfbauth ~/.vnc/passwd -desktop "VNC${USER}@${HOSTNAME}"|grep -Eo "[0-9]{4}">~/.vnc/port.txt

    zenity --info --text="Your VNC port is `cat ~/.vnc/port.txt`"
fi

```
That way when your vncserver gnome-session runs, it will have a $DISPLAY of  :5 (see my earlier post) and will by-pass the x11vnc starting stuff.


I guess I am confused on what this is to do?  it will keep display :5 for a vnc session only and keep display :0 for the physical?

---

### Post by krunge on 2009-12-19
> Sorry, I mean will this new session be able to connect if I just reboot the server?  with vncserver know to run a session on :5 automatically?

I personally would use "crontab" to do this.  This way "vncserver :5" would be run at boottime independent of anyone logging into the gui on the physical display.

You can learn about cron with these commands "man 1 crontab" and "man 5 crontab".

If you run "crontab -e" it will pop you into an editor where you can add new scheduled tasks.  Boy, I hope it pops you into an editor you know how to use...  Then I would add a line like:
```

@reboot   /usr/bin/vncserver :5

```
and then save and exit.  Do all of that as the user you want vncserver to run as.  Then upon reboot vncserver should be automatically started.

---

### Post by krunge on 2009-12-19
> I guess I am confused on what this is to do?  it will keep display :5 for a vnc session only and keep display :0 for the physical?
Yes, that is what I am suggesting.  You use x11vnc for exporting display :0 (the physical display) via vnc, and "vncserver :5" for your virtual (RAM-only) gnome desktop session.

I thought that is basically what you wanted to do, no?

---

### Post by krunge on 2009-12-19
> Also I noticed when I logged into the :5 I got an error window stating 

"An Error occurred while loading or saving configuration information for evolution-alarm-notify. Some of your configuration settings may not work properly.

Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-nYrKIbHNjI: Connection refused)"

I'm not sure what that means, but it looks serious.  Sometimes I get errors saying the sound-card is not working properly, and we don't really expect it to work in the virtual desktop.  However, the above suggests that much GNOME desktop functionality might be not working (do you notice anything not working?)

Here is what "x11vnc -create" tries when starting a GNOME session inside Xvfb:
```

/usr/bin/dbus-launch --exit-with-session gnome-session

```
try putting that in your ~/.vnc/xstartup instead of just "gnome-session".

---

### Post by prettyhatem on 2009-12-19
Alright I did the cron job and the edit to the sharex11vnc script that you mentioned and all worked perfectly as planned on restart!!

Made the change to the xstartup like you mentioned and I didnt see an error.  

Now very last thing!  I wanted to see if I could change my resolution.  When I attempted to open Display under System > Preferences I get a Could not get screen information RANDR exension is not present.  Also to note, I am running an nvidia video card with the nvidia drivers installed.  But when I attempt to run the NVIDIA X server settings app it says that I dont appear to be using the nvidia x driver.  Please edit your X configuration file and restart x server.  If I did this will it effect display :0?

At this point that issue is not really important.  I am just grateful for your help at getting this up and going.  I am really really am thankful!

Also noticing some weird looking fonts... is that normal?

---

### Post by krunge on 2009-12-19
> 
Now very last thing!  I wanted to see if I could change my resolution.  When I attempted to open Display under System > Preferences I get a Could not get screen information RANDR exension is not present.

Run:
```
man vncserver
``` to learn much about vncserver, in particular how to set the geometry:
```

man vncserver
...
       -geometry WidthxHeight
              Specify  the  size  of  the  desktop  to  be created. Default is
              1024x768.
...

```
That may be the only way to change the size.  I don't know if vncserver can be made to support XRANDR for dynamic resizing.
> 
Also to note, I am running an nvidia video card with the nvidia drivers installed.  But when I attempt to run the NVIDIA X server settings app it says that I dont appear to be using the nvidia x driver.  Please edit your X configuration file and restart x server.  If I did this will it effect display :0?

vncserver (and Xvfb) are RAM-only, virtual displays.  They don't use your physical graphics hardware at all, so they couldn't possibly do anything with your nvidia drivers.  I suggest not touching anything nvidia related when you are inside a virtual display.
> 
Also noticing some weird looking fonts... is that normal?
I'm not sure.  I don't use vncserver very much.

---

### Post by batagy on 2010-05-28
Hi Krunge!

I found this thread by search, I just have a quick question regarding x11vnc, and this thread looked general enough to take this question.

So I have running x11vnc as service without any problem (running on Solaris 10 and SLES10 too). I'm using the x11vnc's inbuilt "user chooser" screen (that little black screen), these command line options:

x11vnc -inetd -unixpw -users unixpw= -display WAIT:cmd=FINDCREATEDISPLAY-Xvnc.xdmcp -env X11VNC_CREATE_GEOM=1248x900 (plus a couple of other options that are not interesting here)

My question is related to the wanted VNC screen size. By default, I set the defauls screen size to 1248x900, as can be seen above.

Currently , when a user want to personalize his/her screen size to be started, he can do it this way: when the small black authentication window is appearing first, after his username, he's entering a colon, then specify the wanted resolution in this format: geom=1600x1200.

My question: is it possible somehow to set automatically the preferred screen size, without entering this ":geom=1600x1200" string in the authentication window? I mean to set it per user, without modifying the service options.
I mean, for example setting the X11VNC_CREATE_GEOM or FD_GEOM variables in the user's home ".profile" for example?

(I tried adding these variables to ~/.profile, but it is not taken by the above x11vnc login process.)

This is just a consultation question.
Thanks a lot in advance and congratulation for your amazing x11vnc software.

György

---

### Post by krunge on 2010-05-29
> **batagy said:**
> 
My question: is it possible somehow to set automatically the preferred screen size, without entering this ":geom=1600x1200" string in the authentication window? I mean to set it per user, without modifying the service options.
I mean, for example setting the X11VNC_CREATE_GEOM or FD_GEOM variables in the user's home ".profile" for example?

It might be theoretically possible to do what you want to do with the existing x11vnc; you probably need to use the -display WAIT:cmd=FINDDISPLAY-print and  FINDCREATEDISPLAY-print to print out the scripts and then modify the latter to, say, source the user's preferences (e.g. you would make it ~/.x11vnc_create)

But that might be tricky.

We might be able to add this feature in x11vnc 0.9.11.  However I hesitate due to possible security issues.

I have a couple questions.

You use Xvnc instead of Xvfb.  Is that working OK?  I haven't tried it in years.  Does your Xvnc support RANDR?  If so the user might be able to configure the desired desktop size thru his desktop GUI. Your thoughts on this?

I see you are also using 'xdmcp'.  Presumably the user is supplying his password twice for the first connection?  (i.e once at the little black screen and 2nd at the gdm/kdm/xdm login screen)   I guess this is not a problem for your geometry preferences settings... root has presumably switched to the user before starting the X server directed at xdm.  But it does give rise to some questions about security.

I might be able to add something like FD_USERPREFS=.x11vnc_create, where the user's homedir is prepended and if the file exists it is sourced at the right place. And give a warning to the sysadmin who enables this they are doing it at their risk.

---

### Post by krunge on 2010-05-31
> **batagy said:**
> 
My question: is it possible somehow to set automatically the preferred screen size, without entering this ":geom=1600x1200" string in the authentication window? I mean to set it per user, without modifying the service options.


I made a new thread for the topic related to your question here:

[INDENT][http://ubuntuforums.org/showthread.php?p=9388297](http://ubuntuforums.org/showthread.php?p=9388297)[/INDENT]

I include a new x11vnc feature added based on your question where the user can put the service options in his own preferences file.

---

### Post by mike_perth on 2010-05-31
i notice you're using "gnome-session" in the startup script. when i do this for my virtual vnc window i get all my startup programs running in my virtual window just like in my physical display. unfortunately this is a problem for me (it starts up things like mythTVfrontend and i don't want that running in my VNC window). is there a way to get gnome to start 'differently' in the VNC window, whilst still running as the same user?

regards
Mike

---

