---
title: "VNC viewer doesn't show applications menu"
date: 2012-01-01
forum: General Help
---

### Post by MidnightJava on 2012-01-01
I'm running a vnc server (tightvnc) on Ubuntu 11.04, and viewing it with Screen Sharing on a Mac and also using Chicken of the VNC on the Mac. Everything works fine except that I only see the Terminal window in the VNC session. I don;t see the Unity Desktop.

I ran unity_support_test on the system running the vnc server, and it showed it is supported. I ran the same thing in the VNC session, and it seg faulted. So for some reason, it appears, Unity is not supported in the VNC.

So I changed to Classic desktop, and restarted the vnc server, but I still have the same problem- only a terminal window, no Applications menu. I also enabled remote Desktop access from the Remote Desktop dialog accessed via the System Settings menu.

I'd like to have access to some desktop environment in VNC; I don't care if it's Unity or Classic. How can I make that work?

-Mark

---

### Post by NautilusUK on 2012-03-18
Did you solve this?

---

### Post by MidnightJava on 2012-03-18
I did get it working. Sorry, I forgot to update the post. Below is the contents of ~/.vnc/xstartup.

```
#!/bin/sh

# Uncomment the following two lines for normal desktop:

 unset SESSION_MANAGER

 exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
/usr/bin/gnome-session --session=2d-gnome &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &

```

I think the line
```
/usr/bin/gnome-session --session=2d-gnome 
```

is what fixed my problem. The issue was that 3D sessions are not supported in vnc. I'm running Ubuntu 11.04, and the only 2D session I could find is the one you see above. You may need to implement the equivalent of that command on your system rather than just copy what I have, depending on how your system is configured.

---

### Post by fahyeem on 2013-05-05
Thanks MidnightJava. The solution is to edit the xstartup file as you stated. I want to clarify another point. There are individual xstartup files for every user. For root, the file is located: 
/root/.vnc/xstartup

for other users, the file is in
/home/$USERNAME/.vnc/xstartup

In my case I was editing the user's xstartup file and getting a blank screen in vnc when logged in as root. [COLOR=#ff0000]It is the file
```
/root/.vnc/xstartup
``` that needs to be edited.[/COLOR]

And to be precise, you just need to uncomment the two lines in that file : 

```
unset SESSION_MANAGER
exec /etc/X11/xinint/xinitrc
```

and the line ```
x-window-manager &
```

After uncommenting, run the vncserver as root \\:D/\\:D/\\:D/

---

