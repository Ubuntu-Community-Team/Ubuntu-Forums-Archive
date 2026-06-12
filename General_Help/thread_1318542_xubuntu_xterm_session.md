---
title: "xubuntu xterm session"
date: 2009-11-07
forum: General Help
---

### Post by Lappy 3.0 on 2009-11-07
okay, so my xubuntu box boots into xterm by default (it's a headless box)

is it possible to make it start vnc4server when it logs into xterm like this?  i have to type in "vnc4server" myself every time i turn it on to get everything working.

thanks in advance!

---

### Post by yaztromo on 2009-11-07
Does your server start X windows and login to the desktop automically. Or are you saying that the server just boots to a console?

If it's the former you can just go into settings, session and startup and add the vnc4server command to the application autostart list.

---

### Post by Lappy 3.0 on 2009-11-07
it boots to the console.  more specifically, "xterm" is set as the default session in the login screen, and that's what i get, a black screen with a white terminal box.

---

### Post by yaztromo on 2009-11-07
The only way I can see to do this would be to move away from GDM and use XDM. Then you can use the .xinitrc (or is it .xsession) To autostart programs.

Have a look at this thread [http://www.linuxquestions.org/questions/debian-26/autostart-application-when-logging-into-x-299237/](http://www.linuxquestions.org/questions/debian-26/autostart-application-when-logging-into-x-299237/)

---

### Post by Lappy 3.0 on 2009-11-07
xdm is not working for me.  i think what i really need is to disable all login managers and boot to a console like the server edition of ubuntu.  any idea how i can do that and get vnc4server to run automatically?  or should i just take the time to switch to the server distro (like i should have in the first place (-_-') )?

---

### Post by Lappy 3.0 on 2009-11-07
let me rephrase, if i were to uninstall gdm and use a console login, could i automatically login and autostart  vnc4server without starting xfce?

EDIT: i've got it to boot into a console, but i can't get it to autologin (i tried mingetty, no success) or autostart vnc4server.  i tried putting the command in rc.local, but that didn't work.

---

### Post by yaztromo on 2009-11-08
You could have rc.local start a script:

su -c "/home/yourusername/startvncserver &" yourusername

And in the script make a huge pause to wait for X to start:

sleep 20
vnc4server &

This is probably not going to work for whatever reason. But worth a try.

---

### Post by Lappy 3.0 on 2009-11-09
i got auto-login working, could anyone explain how to use rc.local to run a program at startup to this noob(me)?

---

### Post by yaztromo on 2009-11-10
You could resolve a lot of this hackery by using FreeNX instead:

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

It has resumable sessions, works with GDM, and you don't need to be already logged on at the server when you connect.

And the biggest bonus is its sooo much faster than VNC. :D

---

### Post by Lappy 3.0 on 2009-11-10
> **yaztromo said:**
> You could resolve a lot of this hackery by using FreeNX instead:

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

It has resumable sessions, works with GDM, and you don't need to be already logged on at the server when you connect.

And the biggest bonus is its sooo much faster than VNC. :D

okay, so essentially i can install this and connect to my box using an nx client?  is there an nx client for mac :D?

---

### Post by yaztromo on 2009-11-11
Yep [http://www.nomachine.com/download-client-macosx.php](http://www.nomachine.com/download-client-macosx.php)

---

### Post by Lappy 3.0 on 2009-11-11
well, looks like freenx isn't starting at startup either :(

---

### Post by Lappy 3.0 on 2009-11-27
alright.  there's been some reformatting, reinstalling, blah, blah.  now, my problem is this: [http://i47.tinypic.com/1427tbr.jpg](http://i47.tinypic.com/1427tbr.jpg)

it won't start an x session properly when i vnc to it.  any ideas?

update:  ssh also stops responding after a period of time, and i don't know why.

---

### Post by Lappy 3.0 on 2009-12-05
bump

---

### Post by Lappy 3.0 on 2009-12-21
i've fixed vnc, but everything cuts out after a period of time, all services just stop responding (ssh, vnc, afp, etc)  any help is much appreciated!

---

