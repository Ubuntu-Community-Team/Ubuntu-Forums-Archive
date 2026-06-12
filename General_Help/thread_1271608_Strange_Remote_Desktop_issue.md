---
title: "Strange Remote Desktop issue"
date: 2009-09-21
forum: General Help
---

### Post by fatgeek on 2009-09-21
I have my desktop set up to allow connections via the built in Remote Desktop.  I am able to log in fine, but, while I am able to control the desktop remotely from my laptop it doesn't show me that I am doing so.  Confusing, I know, so here is an example:

I am sitting next to the desktop using my laptop.  I am logged into the desktop via remote desktop from my laptop.  I move the mouse cursor on the laptop and I am able to control the desktop's cursor but nothing else. Nothing else reacts.  I can't click buttons, I can't drag windows.  However, (and here's the kicker) When I look at the desktop's screen I see everything happening that I'm doing on the laptop.

For some reason the laptop isn't showing me updated images from the desktop.  (I think).  I'm running Jaunty on the desktop and Intrepid on the laptop if it makes a difference.

Any help figuring this one out would be appreciated.

---

### Post by XCan on 2009-09-21
It's a bug in Jaunty, and also, as far as I know, in Karmic. The simple workaround is for you to disable visual effects. 

You can also use a vnc server supporting xdamage flag, or patch Xorg yourself. More details: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126)

---

### Post by asphixmx on 2009-11-11
Confirmed, I have Karmic Koala and the bug still exists. There was no bug in Intrepid Ibex and before. You have to disable de compiz manager in the server and then from the client you can see the screen refresh and use it normaly. I found a simple workaround to disable compiz from the remote machine:
First, install xbindkeys and xbindkeys-config in the server. This is for assigning a command or launch a program from a keystroke shortcut you configure. Then assign to some keys (I assigned the CTRL-SUPER (windows key)-M) to a command "metacity --replace". Then, when you connect from the remote machine, just press CTRL-SUPER-M and voila, the compiz on the remote machine is disabled and you can work remotly.
It is not a fix, just a workaround the problem.
Greetings.

---

