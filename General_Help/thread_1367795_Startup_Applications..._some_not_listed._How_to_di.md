---
title: "Startup Applications... some not listed. How to disable?"
date: 2009-12-29
forum: General Help
---

### Post by User0123 on 2009-12-29
Something like privoxy or tor isn't listed in the GUI for controlling Startup Applications. I don't want it running every time I boot, I'd rather control it with Vidalia.

What's the other way to stop it running on startup?

---

### Post by User0123 on 2009-12-29
I presume I can just edit a file or script somewhere? Just wondering where that somewhere is :P

---

### Post by cybergalvez on 2009-12-30
I would assume its an init script, take a look in etc/init.d

---

### Post by dcstar on 2009-12-30
> **User0123 said:**
> Something like privoxy or tor isn't listed in the GUI for controlling Startup Applications. I don't want it running every time I boot, I'd rather control it with Vidalia.


"Startup Applications" only applies to GUI apps launched when you log into the GUI, not system processes that start up at boot-up.

As the others have said, you have to look at the startup scripts, but if they are in those scripts they are there for a (usually very good) reason and usually don't take kindly to someone mucking around with them.

Also check System-Administration-Services.

---

### Post by spigy11 on 2009-12-30
Hi There

There are two ways of going this

the gui-way

System - Preferences - Startup application 

the other way is via CMD with update-rc.d

so for example to disable apache - sudo update-rc.d apache disable 5 - disables to start apache in runlevel 5, runlevel 5 is the X11 or graphical GUI in which U usually works with ubuntu.

Hope that helps

---

### Post by 3rdalbum on 2009-12-30
> **spigy11 said:**
> Hi There

There are two ways of going this

the gui-way

System - Preferences - Startup application

It's not in Startup Applications, that's the whole point of this thread.

---

### Post by spigy11 on 2009-12-30
so the second choice then :)

there is a ubuntu-howto

[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

take also a look at

[http://www.cyberciti.biz/tips/how-to-controlling-access-to-linux-services.html](http://www.cyberciti.biz/tips/how-to-controlling-access-to-linux-services.html)

the startup scripts for runlevel 5 should be located in /etc/rc.5 folder

---

### Post by Carbs70 on 2010-02-06
Have had a look around for information on this same problem, but can't seem to find anything.

When installing 9.10 I played around for a while to get a desktop that worked well for me, and ended up with a 4x1 cube (which is probably pretty standard).

Then I tried to get Ubuntu to startup all the applications that I need for my programming work on boot - hoping that they would also remember which face of the cube they belonged in.

That didn't work, with all apps getting spawned onto the one face, so I removed them all from the startup.... except that I have 3 apps still starting up which aren't on the System -> Startup Apps list: Firefox, Kate, and a Nautilus window pointed at my home dir.

To compound the problem, when Kate fires up it is totally inoperative - I actually need to close it and reopen it before it works anyway.

If anyone can tell me how to remove these from startup I'd be stoked. I'm comfortable with terminal if thats what I need to do, but the problem is knowing actually what needs to be done! The links provided above really told me nothing that I could use....or at least didn't give me any clues of how I might extend them to my own problem.

To take it one step further, if anyone can tell me how to startup applications on different faces of a cube, that would be awesome!

---

### Post by Carbs70 on 2010-02-10
Found this, which solves one of my problems
[http://www.ubuntu-inside.me/2009/06/howto-make-applications-start-in.html](http://www.ubuntu-inside.me/2009/06/howto-make-applications-start-in.html)

Now I just need to know why Firefox, Kate and Nautilus all open at startup even when they are not listed as a startup application.....   any ideas?

---

### Post by rifter on 2010-04-07
> **Carbs70 said:**
> Found this, which solves one of my problems
[http://www.ubuntu-inside.me/2009/06/howto-make-applications-start-in.html](http://www.ubuntu-inside.me/2009/06/howto-make-applications-start-in.html)

Now I just need to know why Firefox, Kate and Nautilus all open at startup even when they are not listed as a startup application.....   any ideas?

You probably have the setting enabled to remember previous sessions. Even of you don't, I have noticed that if you had it on before it can get stuck.  

First check System -> Preferences -> Startup Applications -> options.

There you will see the checkbox to remember running applications when logging out.  Make sure that is unchecked, then hit  Close.

Now for me I once got stuck where even though I unchecked that box the applications kept coming up.  I seem to recall that I later got some things corrupted and had to login under the failsafe session, set that setting, and relogin with a regular session.  

If that does not work you could probably logout and delete the session files; they are stored under ~/.gnome2/session

The fact that the stored sessions are not deleted when you uncheck that box is a _[color=blue][bug, which makes this possible](https://bugs.launchpad.net/gnome-session/+bug/34321)[/color]_.  In other words it would not be possible for the applications to startup when you don't tell them to if the sessions were deleted when you unchecked that box.

---

