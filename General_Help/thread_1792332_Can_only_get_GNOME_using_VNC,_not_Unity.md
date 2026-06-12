---
title: "Can only get GNOME using VNC, not Unity"
date: 2011-06-28
forum: General Help
---

### Post by haydnw on 2011-06-28
Hi,

I've recently installed 11.04 and it's working OK. I'm having a bit of trouble getting Unity to work over a VNC connection. At the moment I'm using VNC Server and it lets me connect over the LAN without any problems, but I get GNOME instead of Unity. I've followed instructions on a couple of pages:

[http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_11.04_Unity_Desktop#Attaching_to_a_Remote_Unity_Desktop_using_vncviewer](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_11.04_Unity_Desktop#Attaching_to_a_Remote_Unity_Desktop_using_vncviewer)

[http://ubuntuforums.org/archive/index.php/t-1763285.html](http://ubuntuforums.org/archive/index.php/t-1763285.html)

But these don't seem to have made any difference. My VNC server settings file currently looks like this:

```
#!/bin/sh

unset SESSION_MANAGER
. /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &

```

I may be missing something really obvious, but if someone could enlighten me I'd be very grateful!  :)   Thanks.

---

### Post by An Sanct on 2011-06-28
In my experiences (under Windows), VNC was really laggy even tho I had a T10 connection (with a 1gb ethernet connection) and it didn't want to transfer more than 800*600 in 256 colors also it switched off themes and anything graphical...

On the other hand, Unity is a 3D high resolution - "millions and gazillions of colors" thingie ... Has anyone ever gotten Unity over VNC running???

---

### Post by haydnw on 2011-06-28
This is running over a GbE connection - not getting any error messages or anything which would suggest that a lack of bandwidth is what's causing the problem.

---

### Post by An Sanct on 2011-06-28
Well, my connection was also 1Gb to server and company optical from there ...

As I said, Unity is a graphics "hog" :) it wants a good graphics card in the machine, where it runs (the host), has the host got a Unity *compatible* GPU?

ps. sorry, my keyboard stops working from time to time ... i had to reboot to finish this post.

---

### Post by haydnw on 2011-06-28
Yep - if I log onto the machine locally then I get the full Unity experience. It's just when I connect over VNC that I'm forced into GNOME.

---

### Post by An Sanct on 2011-06-28
Take a look [here]("http://www.roytanck.com/2011/06/16/having-trouble-with-vnc-and-unity-try-this/") :)

---

### Post by haydnw on 2011-06-28
Thanks - have already tried that with no luck. He already has a connection to Unity, it's just slow. I cannot connect to Unity at all, I just get GNOME each time. The connection speed is fine.

---

### Post by haydnw on 2011-06-30
No more suggestions? Surely somebody must have Unity running over VNC?  :(

---

