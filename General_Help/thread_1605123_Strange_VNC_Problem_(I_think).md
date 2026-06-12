---
title: "Strange VNC Problem (I think)"
date: 2010-10-24
forum: General Help
---

### Post by SanDiegoSeahawk on 2010-10-24
I rebooted my 10.4 Ubuntu machine but didn't log back into it before I attempted to connect to it via VNC from my Mac.  The VNC connection was refused (which I think is right since I wasn't logged into the Ubuntu host).

The problem:  The Ubuntu machine console is inactive.  Its as though the system is directing the display elsewhere.  If I reset the machine, the display is active up to the point where Ubuntu loads and normally would display the login screen.  I hear the little drum beat after the screen goes dark.

Seems like VNC has messed up my root display.

Anybody have any idea how to correct this?  I can ssh into the machine from another machine.

Any help would be greatly appreciated.

thanks.

---

### Post by SanDiegoSeahawk on 2010-10-24
I can ctrl-alt-f4 and kill X and get a console login.

It really seems like the default display for X is hosed.  Anybody know how to figure out where X thinks its displaying or where its saved?

thanks.

---

### Post by SanDiegoSeahawk on 2010-10-24
Just realized this isn't killing X, its just creating a console login for tty4.

I'm stumped.  It seems like the system has saved a bogus display for X but the life of me I can't figure out where this would be.

Any help?

---

### Post by SanDiegoSeahawk on 2010-10-25
So, I'm able to ssh into the machine and stop gdm.  This gives me a text login screen on the Ubuntu host.  Once logged in, I can run startx which causes my display to go blank and the monitor actually goes into standby mode.

Now I can VNC from my mac is everything looks good.  I don't see any errors, the XServer settings seem good, the display is detected correctly and everything.

It really seems like somehow X has lost its mind with regards to the default display.

I'm sure there is a simple fix for this.  Can anybody throw me a bone on his one?

thanks.

---

### Post by HermanAB on 2010-10-25
Howdy,

Since you have SSH working, why waste your time with VNC?

$ ssh -X -C -c blowfish user@linuxmachine gnome-panel

Any program you launch fro the remote panel, will run transparently on the local desktop.

---

### Post by SanDiegoSeahawk on 2010-10-25
So the latest with this is now when I remotely stop GDM I don't get a non-graphical login prompt on the console.  This is particularly problematic as I cannot run startx and connect to it remotely via VNC.

I originally thought the problem was VNC related but now I'm thinking its GDM related.

I saw some posts regarding nVidia drivers and symptoms similar to this and was going to try to update drivers but now I'm not sure how to do that without an Xsession to run the update tool.

Any thoughts on why GDM would be having a problem running on the local host display?

---

### Post by HermanAB on 2010-10-25
If you use SSH to run graphical programs remotely, then you don't need to run the GUI so you don't need to debug GDM or X.

---

### Post by SanDiegoSeahawk on 2010-10-25
> **HermanAB said:**
> If you use SSH to run graphical programs remotely, then you don't need to run the GUI so you don't need to debug GDM or X.

I understand that.  I didn't mean to imply that I don't need the console on the computer, I do.  I'm using it for development.   I can't just ignore the problem.

thanks though.

---

