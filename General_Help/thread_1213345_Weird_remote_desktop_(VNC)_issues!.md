---
title: "Weird remote desktop (VNC) issues!"
date: 2009-07-14
forum: General Help
---

### Post by dtemp132 on 2009-07-14
So Remote Desktop (VNC, default vino server) is sorta working but not really.

I connect to my machine (9.04 desktop) and the client computer can move the mouse and click on stuff, and the keyboard works... but the screen doesnt redraw on the client!  So, for example, I can move the mouse and click on a menu item, and looking at the monitor attached to the system, I can see the mouse move and the menu open... but on the client, the screen stays the same, and I cannot see the opened menu.  I can continue to move the mouse and click on stuff on the client, but I am unable to see what I am clicking on because the display is "frozen" at the state it was when I first logged in to VNC.

I tried reinstalling the vino package, no help.  It worked fine in 8.10 before I upgraded.  Tried rebooting several times, no help.

Definitely seems like a bug to me.  Anyone have any advice?  I primarially use this computer in a headless manner, and I'm only marginally SSH capable, so having this graphical remote interface is pretty necessary to me.

---

### Post by dtemp132 on 2009-07-14
Fixed my own issue.  Apparently I had to set Visual Effects to None.  Sounds like some complicated issue from the combination of VNC, X, and Nvidia.  Grrr.

---

### Post by HermanAB on 2009-07-14
Here you go:
ssh -X -C -c blowfish user@server gnome-panel

---

### Post by XCan on 2009-07-15
There are some additional crappy workarounds concerning disabling xdamage described [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126) . 

> **HermanAB said:**
> Here you go:
ssh -X -C -c blowfish user@server gnome-panel

That's not the same, and I haven't figured out how, if possible, to make it the same. Some people do require to continue working on whatever it was they had opened on their desktop.

---

### Post by Pritamsng on 2009-07-24
Hi, All,
Actually i m trying to configure **[COLOR=#ff0000]vnc[/COLOR]** **[COLOR=#ff0000]server[/COLOR]**(multi user) on **[COLOR=#ff0000]ubuntu[/COLOR]**.. its working fine but one problem i m getting that is from the client system when i m connect to **[COLOR=#ff0000]server[/COLOR]** through **[COLOR=#ff0000]vnc[/COLOR]** i cant able to get the g[FONT=Times New Roman][SIZE=3]raphic.. a screen shoot i m attetching here. please any one can solve my prob then replay [/SIZE][/FONT]
[IMG]http://i620.photobucket.com/albums/tt288/pritamsng/vncprob.jpg[/IMG]

---

### Post by Pritamsng on 2010-02-10
He i got the solution,
just write "sh" in place of "exec"

---

