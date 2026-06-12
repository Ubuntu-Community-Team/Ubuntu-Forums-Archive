---
title: "xstart new  xubuntu session"
date: 2011-05-06
forum: General Help
---

### Post by wadedesk on 2011-05-06
I'm running Ubuntu 11.04 but have customised the desktop to a reverse white on black theme that I use for presentations.  I've installed xubuntu-desktop and would like to be able to start a new session after I've logged into my standard Gnome desktop.  I've read some other help files, but so far have not be able to get xubuntu-desktop running in a new window.  I'm having problems just getting a new session of x server running, let alone xubuntu.  Any help would be appreciated.

---

### Post by wilee-nilee on 2011-05-06
> **wadedesk said:**
> I'm running Ubuntu 11.04 but have customised the desktop to a reverse white on black theme that I use for presentations.  I've installed xubuntu-desktop and would like to be able to start a new session after I've logged into my standard Gnome desktop.  I've read some other help files, but so far have not be able to get xubuntu-desktop running in a new window.  I'm having problems just getting a new session of x server running, let alone xubuntu.  Any help would be appreciated.

I think you can't run both desktops at the same time, a virtual would be probably your choice. You can logout of the desktop to the other as well.

You could go to tty kill the desktop and start xubuntu, but I don't know the commands others will, if this works.

---

### Post by sisco311 on 2011-05-06
You should be able to start a new xubuntu session on vt10 (Ctrl+Alt+F10) with:
```
startx ck-launch-session /usr/share/xubuntu/session.sh -- :10 vt10
```

---

### Post by wadedesk on 2011-05-06
When I copy the code 
```
startx ck-launch-session /usr/share/xubuntu/session.sh -- :10 vt10
``` 
and paste it into Terminal, I get message that I do not have permission.  
If I precede the code with "sudo", the screen goes black.  I do not think that it is locked up, but no key combinations that I tried would close the open window.
I tried Ctl+Alt+F10 and I get a black screen with a fast flashing curser.  I'm not able to type any thing into the window, but Ctl+Alt+Del will reboot the system.

---

### Post by sisco311 on 2011-05-06
I forgot to say that the first X session runs on vt7 or vt8, so you can switch back to it by pressing Ctrl+Alt+F7 or Ctrl+Alt+F8.

By default, only console users are allowed to start a new X server. So you either switch to virtual terminal (there are six by default, Ctrl+Alt+F1 will switch you to the first, Ctrl+Alt+F2 to the second and so on), log in and run the command from there or if you want to allow any user to start an X server, then run:
```
sudo dpkg-reconfigure x11-common
```
an follow the instructions.

And NEVER run startx as root (with sudo). It will start the whole session as root, which is a very bad idea.

Oh, and you may have to specify the full path to the ck-launch-session command:
```
startx /usr/bin/ck-launch-session /usr/share/xubuntu/session.sh -- :10 vt10
```

---

### Post by wadedesk on 2011-05-07
I has some success with the virtual server.  I'm able to CTL+ALT+F1 and switch to the virtual server.  I'm able to login and launch XFCE using the long code supplied.  However, if I CTL+ALT+F7 to my Gnome desktop and then switch back using CTL+ALT+F1, XFCE has crashed and I have a screen full text.

The only thing that is non-standard on my Ubuntu desktop is Docky.  I'm running it instead of the bottom panel.  If I log into XFCE normally, Docky runs over top of the XFCE bottom menu and seems to functional normally.  However when I run SFCE in a virtual server, Docky is static on the bottom of the desktop and the standard XFCE menu will appear and hide as I move the mouse to the bottom of the screen edge.

Could Docky be causing the crash or is there something else?

Would reconfiguring x server solve the problem that I'm encountering with the virtual server?

I've been running Ubuntu for a while, but just now trying to use some of the power features of Linux as I started doing presentations on my laptop.

Thanks for any additional suggestions.

---

### Post by wadedesk on 2011-05-07
I tried disabling Docky on start-up and rebooted my system.  I can CTRL+ALT+F! and start XFCE in a virtual server.  However when I switch to Gnome using CTRL+ALT+F7 and then back to XFCE it crashes.  I want to be able to run the XFCE desktop and Gnome and switch between them as I work if this is possible.

---

### Post by wadedesk on 2011-05-07
After changing the .conf file for xserver and allowing "anyone" to start the server, I ran the command one more time.  It starts XCFE on F10.  

Now I'm able to switch from Ubuntu desktop by pressing CTRL+ALT=F7 to Xubuntu desktop by pressing CTRL+ALT+F10 and back with no problems.  

If I'm streaming Internet radio in Ubuntu, it continues to play even when working in Xubuntu desktop.  Thanks!  This is exactly what I wanted.

---

