---
title: "Getting a window manager on X.org :0 when Xgl is running on :1"
date: 2006-06-21
forum: General Help
---

### Post by Robb Kidd on 2006-06-21
I've opted to run Xgl on :1 by calling it from .Xsession as follows:

```
.Xsession
#!/bin/sh
# Start up Xgl, compiz, and GNOME
# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1
# Start Compiz window manager
gnome-window-decorator &
compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &
# Start GNOME
xmodmap -e "keycode 22 = BackSpace BackSpace"
exec gnome-session
```

Works great.  Love the eye-candy.  

However, the occasional program does not like Xgl.  For example, totem-xine and some games are much happier running on the X.org server I still have available on :0.  But when I direct these programs to display :0, they lack a window manager and so are borderless, unmanagable and stack in the upper left corner.

Is it possible to provide a window manager for :0 as well?  I've tried calling metacity in .Xsession before Xgl, but then Xgl runs within a metacity window.

**SOLUTION:** Devil's Pie (package: devilspie)

Solved!  \\:D/

*Update:* Sorta.  I've dropped calling metacity on X.org :0 and use Blackbox.  Now ALT-Click moves the whole borderless Xgl window instead of windows running *on* the Xgl server.

Shockingly simple once I found the right keywords to feed Google. A package called devilspie provides the means to remove the window decoration for Xgl running on top of X.org.  Now graphically intense things like games and movies that do not like Xgl can be sent to X.org with borders!

The new .Xsession:
```
#!/bin/sh
# Devil's Pie will nix the Metacity window decoration for Xglx
**devilspie  &**
# Start Metacity for X.org on :0 
**metacity &**
# Start up Xgl, compiz, and GNOME
# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1
# Start Compiz window manager
gnome-window-decorator &
compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &
# Start GNOME
xmodmap -e "keycode 22 = BackSpace BackSpace"
exec gnome-session

```

In ~/.devilspie/xglx.ds:
```
 (if (is (application_name) "Xglx") (undecorate)))
```

---

### Post by Robb Kidd on 2006-06-21
Update:

Not news to those of you in-the-know, but when I run metacity from a terminal after exporting DISPLAY=:0, Xgl is wrapped by the new window manager.  Curses.

---

### Post by Robb Kidd on 2006-06-21
Solved!  \\:D/

Shockingly simple once I found the right keywords to feed Google. A package called devilspie provides the means to remove the window decoration for Xgl running on top of X.org.  Now graphically intense things like games and movies that do not like Xgl can be sent to X.org with borders!

---

### Post by grendelkhan on 2006-06-21
I use the nonXgl scripts I found in a thread on this forum - works like a friggin champ.

---

### Post by Jott on 2006-06-21
Hi - 

could you post the link to the non-xgl scripts thread if you have it handy?  I did a quick search and didn't find it, I'm hoping not to have to sift through all 432,198 posts in the main xgl thread...

thanks!

---

### Post by Robb Kidd on 2006-06-21
Clever people.  

Not sure that it would work for me.  I already have the ability to send to the X.org server on :0 with a simple "export DISPLAY=:0".  My issue, and according to one screenshot in the nonXgl thread it is an issue there as well, is window decoration on the :0 windows.

Is this a problem for you?

Since my last update, I dropped metacity for blackbox, but now ALT-Click moves the entire borderless Xgl window, not buttonless windows running on the Xgl server.  I'm looking at Fluxbox and it's Xnest option to ignore Fluxbox keybindings, but the US Ubuntu mirror is 403ing me.

References: [nonXgl thread]("http://www.ubuntuforums.org/showthread.php?t=176636")

---

### Post by grendelkhan on 2006-06-21
[QUOTE=Robb Kidd]Clever people.  

Not sure that it would work for me.  I already have the ability to send to the X.org server on :0 with a simple "export DISPLAY=:0".  My issue, and according to one screenshot in the nonXgl thread it is an issue there as well, is window decoration on the :0 windows.

Is this a problem for you?
[/QUOTE]
I just got lazy and didn't feel like spawning another server full time and toggling between display 0 and 1. 

Potayto - Potahto

[QUOTE=Robb Kidd]
References: [nonXgl thread]("http://www.ubuntuforums.org/showthread.php?t=176636")[/QUOTE]

That's the one.  Been happily playing Enemy Territory and UT2004 ever since.  Made me a darn happy man.

---

### Post by Robb Kidd on 2006-06-21
I am fairly lazy as well.  When I started this thread, I'd been using the Dapper Xgl and compiz packages.  After adding the beerorkid.com and compiz.info repositories and upgrading, the ALT-Click to move some windows requirement was happily overcome by events. 

I've made a new panel launcher for gnome-terminal with the --display=:0 switch from which I can run my games and movies.  And Blackbox is content to wrap the windows I sent there.

I'm pretty happy.  I'm still looking for a lighter window manager to run on :0.  No keybindings, no menubar/taskstrip/commandwidget, single workspace sort of thing

---

