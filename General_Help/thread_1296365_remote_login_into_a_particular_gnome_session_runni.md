---
title: "remote login into a particular gnome session running on the machine"
date: 2009-10-20
forum: General Help
---

### Post by driftingprogrammer on 2009-10-20
using the command gdmflexiserver i can have multiple GNOME sessions on my desktop between which i can toggle using keys like Alt+Ctrl+F7 and Alt+Ctrl+F9.

So two different users can be logged into Gnome at the same time.

My question is when i access the Remote Desktop from any vncviewer how can i choose the terminal i want to access i.e. wether i want to see the terminal on Alt+Ctrl+F7 or Alt+Ctrl+F9.

If i use vnc4server i get completely new sessions whereas i want to connect to one of the sessions running on the terminal (where i have my unsaved work).

Please help i have read through many blocks but could not find anyone attempting this, that is accessing your Remote Desktop when some one else is using the machine over a different terminal.

---

### Post by Giblet5 on 2009-10-20
This is similar to using Windows' remote desktop from a Windows virtual machine to a Windows server: ya gotta give that remote server a CtrlAltDel to log in, but there's no way to route those keystrokes the way you need to.

Until the vnc and vm crowd address keystroke-routing gracefully, the best answer is "don't do that".

Wish I had a better answer.

---

### Post by driftingprogrammer on 2009-10-20
Could this bug in vino be stopping me from achieving the above or is there anything in the below bug report that can help me achieve what i want -->
------------------------------
I filed this with Ubuntu here:
[https://bugs.launchpad.net/ubuntu/+source/vino/+bug/394318](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/394318)
And was told to refile upstream. I have not tried onn Gnome 2.28.

Upgraded from Ubuntu 8.10 to Ubunttu 9.04, where it used to work fine. Running
dual monitor on separate xservers. When I connect to port 5901, the connection
stalls on the first try and is refused on successive attempts. Connections to
port 5900 show the contents of screen ':0.0' but controls EITHER ':0.0' or
':0.1', depending on location of cursor local cursor. (When cursor on display
:0.0, connected client controls display :0.0. When cursor on display :0.1,
connected client controls :0.1, though client ALWAYS views :0.0's contents.)

Expected behavior (expressed in Gnome 2.24):
Connecting to 5900 shows and controls :0.0; connecting to 5901 shows and
controls :0.1. This should occur regardless of the location of the local
machine cursor (moving the local mouse shouldn't change where a connected
client's mouse clicks are registered. Additionally, there should never be a

----------------------
case where connected clients see the contents of one display but controls
another.

vino 2.26.1-0ubuntu1
nvidia-180-kernel-source 180.44-0ubuntu1
display 0.0 is vga, 0.1 is svideo
uname: 2.6.28-13-generic i686

I know some bugs in vino can be nVidia binary driver specific. I have not tried
using 2 VGA monitors and an OSS driver as I do not have a second display handy
and S-Video only works in the binary driver.

---

### Post by driftingprogrammer on 2009-10-20
Is it possible to get multiple vino running on different ports connecting to different terminals.

Saw the following comment and wondering if there are any hints here ->

If you look in the vncservers file it explains how to setup multiple
desktops. 0: is there by default (served by vino) but you can setup as
many as you want and access them by their screen number ie. 5900:3 to
get to screen 3.
Note that the file locations I quoted are for Fedora
Reply With Quote 

from [http://fixunix.com/ubuntu/392328-remote-desktop-login-8-04-a-2.html](http://fixunix.com/ubuntu/392328-remote-desktop-login-8-04-a-2.html)

---

