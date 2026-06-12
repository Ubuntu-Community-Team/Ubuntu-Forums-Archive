---
title: "FreeNX Problems"
date: 2006-01-29
forum: General Help
---

### Post by nickc on 2006-01-29
Hey All,

I am having trouble with FreeNX, I've installed as per:

[https://wiki.ubuntu.com/FreeNX](https://wiki.ubuntu.com/FreeNX)

Using default NX keys and package from "deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas freenx" repository. I am running Breazy:

# uname -a
Linux nibiru 2.6.12-10-386 #1 Thu Dec 22 11:37:10 UTC 2005 i686 GNU/Linux

Now the install goes fine:

root@nibiru:~# dpkg -l | grep nx
ii  freenx                                 0.4.4+0.4.5-3ubuntu0               The FreeNX application/thin-client server ba
ii  nxagent                                1.4.92+1.5.0-4ubuntu0              NoMachine NX - nesting X server with roundtr
ii  nxlibs                                 1.4.92+1.5.0-4ubuntu0              NoMachine NX - common agent libraries

And I can connect to the box just fine. The problem occurs when I exit a session and click "suspend". When I resume the session (From official Windows NoMachine client) the NX window takes up the entire screen (With a big black border around it),I can't click anything and I have to kill the process through taskmanager. If I then try to reconnect, it starts a fresh session and all is OK untill I try to resume again. 

It's a bit hard to explain the problem so I've uploaded an screenshot showing what I mean:

[www.tim.nildram.co.uk/freeNX-resume.jpg](www.tim.nildram.co.uk/freeNX-resume.jpg)

Any ideas what's wrong?

---

### Post by nickc on 2006-01-29
I've also noticed, that window that is "shrunk" in the top left corner is actually a NoMachine client and if I expand it I can get at my desktop OK. So it seems the great big one that takes up all my screen is just a static image of the desktop... 

Really weird, anyone else seen this?

---

### Post by dumpster25 on 2006-02-03
Yeah I got the same problem too, I just don'tknow where to start looking, the freenx.log file in /var/log doesn't tell me much. In fact in doesn't tell me anything :confused:

---

### Post by g-a-c on 2006-02-03
One of the lecturers at my university had this problem, and after we both tried a bit of troubleshooting we finally came up with this "solution":

> Apparently, there are known bugs with nx/client. To establish, run, suspend and recover succsfully a (persistent) session, yoiu *must* configure the client for full-screen operation. When you start your session, things are fine; to suspend it, click the 'invisible pixel' at top-right corner (M$ client). This will minimize the local client or somehow, use the ability to select 'close'. When you do that, the remote server will ask you whether to suspend or terminate; suspend means that you enter persistent mode, with all your goodies running in the background.

I guess, this will keep me ticking for a while - please pass the message: *fullscreen only*It's not perfect, but it seems to be the only way we could get FreeNX to work reliably in a hurry (was just hours before finishing for Christmas). This was using

nx-1.5.0-0.FC3.1
freenx-0.4.4-1.fdr.0

on a Fedora Core 3 box, and the latest nxclient of the time (1.5.0)

---

### Post by dumpster25 on 2006-02-04
Thanks gavinchappell :) 

Your solution seems to work out. Before when I got that problem I could'nt even terminate thesession from the client even if I tried the keyboard shortcus. Instead, I had to go and kill the nx session on the server itself.

As I said it now works fine if I run it in fullscreen mode. And I suppose I can run in fullscreen mode in the future, it doesn't bug me anyway. Thanks again :mrgreen:

---

