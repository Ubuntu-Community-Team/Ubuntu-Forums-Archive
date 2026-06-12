---
title: "Alternative to VNC"
date: 2010-02-03
forum: General Help
---

### Post by ktz84 on 2010-02-03
Hi,

I'm using vnc to connect to my ubuntu box from my windows box however I don't like the way it works.

1) It doesn't start automatically. I have to be logged into my username before I can connect to my box.

2) It takes control of the screen on my ubuntu box which isn't what I really want to happen. I'm used to connecting via rdp in windows where I connect to the other computer and if you looked at the other screen you wouldn't even know I am logged on. This is handy if someone else is using the pc plus I just don't like everything that I am doing to appear on a computer screen that I can't see. I find it kind of freaky.

Can I achieve these in Ubuntu and if so what am I looking for.

Hope that makes sense.

---

### Post by bjeagle on 2010-02-12
I use this to connect to my Ubuntu 9.10 - the Karmic Koala from my Windows XP

[LIST=1]
[*]I use PuTTY to connect to the box over SSH and I have a tunnel (port forward) setup which I connect to the VNC server
SSH server is installed on the box by
```
sudo apt-get install openssh-server 
```
[*]Install vncserver
```
sudo apt-get install vnc4server xinetd
```
[*]Edit the default xstartup
```
gedit ~/.vnc/xstartup 
```I have the following in my xstartup
```
#!/bin/sh
# Uncomment the following two lines for normal desktop:
#unset SESSION_MANAGER
#exec /etc/X11/xinit/xinitrc
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
#xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
eval `dbus-launch --sh-syntax --exit-with-session`
gnome-session &
#twm &
```
[*]Start a new server
 ```
vncserver -depth 24 -geometry 1440x900 -name bjeagle
```First time you run vncserver you are requested to provide a password.
The output will tell you which port to connect to.
The first server will be available on port 5900 unless its already occupied, next will be 5901, ... It will say something like
```
New 'bjeagle' desktop is server:1
```You can start as many new server as you like with different resolutions 
 ```
vncserver -depth 24 -geometry 1920x1200 -name bjeagle
```...
After each reboot I do this 4th step manually, I don't like having VNC servers hanging around if I'm not using them
[*]Start your vnc client and connect to either of your new vnc server sessions or all at the same time :P
[/LIST]

---

### Post by fisheater on 2010-02-12
Nice easy alternative is Nx Nomachine: [http://nomachine.com/](http://nomachine.com/),  [http://ubuntuforums.org/showthread.php?t=941530](http://ubuntuforums.org/showthread.php?t=941530)

The beauty of it is that it doesnt take control of your screen, it spins up a virtual copy of your computer, is encrypted by default, and was super easy to install. That said, I am having trouble getting my file share to work. Other than that is has been superb.


To access from windows box: download windows client from Nx

To access from any windows + your usb: [http://blog.galerie-cesar.com/download-portable-version-of-nxclient-for-windows/](http://blog.galerie-cesar.com/download-portable-version-of-nxclient-for-windows/)

GL

FE

---

### Post by gmargo on 2010-02-12
> **bjeagle said:**
> You can start as many new server as you like 


I do a similar thing to start KDE sessions.  With KDE (KDE-3.5 at least on Hardy and Debian Lenny), you can set the KDEHOME environment variable so that most KDE settings can be kept separate from other simultaneous sessions.  Is there a similar way to configure GNOME?  Don't you end up with multiple GNOME sessions all trying to use the same gconf database?

---

### Post by bjeagle on 2010-02-12
Short answer: I don't know but it seems to work. 
What can happen if the gconf database used by multiple sessions?

---

### Post by gmargo on 2010-02-12
> **bjeagle said:**
> Short answer: I don't know but it seems to work. 
What can happen if the gconf database used by multiple sessions?

I don't really know.  I expect that multiple sessions would look identical and that changes made to one would show up in the other (either immediately or after a restart).  Take a look at the output from "gconftool-2 -R /desktop" and you can see the sorts of settings that are stored there.  Just to name one thing, what if I want a different background image in different sessions?

---

### Post by sergey1369 on 2013-03-23
I was on TeamViewer for two years, but now have found one more great alternative - Splashtop 2. 
Very fast, lightweight, can Stream video, faster then NX (on asus eee 1000), have ANDROID client. 
The only annoying downside - no linux client yet (only server part).

---

### Post by QIII on 2013-03-23
Thank you for sharing.  Everyone’s questions are important and answers are valuable.

&#65279;If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

*Thread** closed.***

---

