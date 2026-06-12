---
title: "another 'your session only lasted less than 10 seconds' problem"
date: 2010-04-07
forum: General Help
---

### Post by JazzBluz on 2010-04-07
I was messing with network settings, then started to get this error once i get to the graphical GNOME login:

Your session only lasted less than 10 seconds.  If  you have not logged out yourself, this could mean that there is some  installation problem or that you may be out of diskspace.  Try loggin in  with one of the failsafe sessions to see if you can fix this problem.

and then the details (~/.xsession-errors file)

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for local=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to  /etc/X11/xinit/xinput.d/default.

SESSION_MANAGER=local/optiplex:/tmp/.ICE-unix/5534

the underlying file system and Debian OS seems to be fine as I can log into the failsafe terminal with no problems and see files ok...

I have already tried resetting permissions on /tmp and disabling ivp6, but the problem continues...

Someone please help...

---

### Post by sirius1 on 2010-06-15
Hello!
Did you ever find a resolve to this issue?

I have done days and days of reading on it and come away with a few things. These files can affect the gnome autostart:

.gconfd
.gconf
.gnome2
.gnome2_private
.config

I just wish I new which one of them to delete. I read you can delete all of them, but I know if you do --you will delete your custom panels to.

Then I read something about the .xsession file, deleting this file resolved the problem for one person. [http://ubuntuforums.org/showthread.php?t=882717&highlight=session+lasted+10+seconds&page=2](http://ubuntuforums.org/showthread.php?t=882717&highlight=session+lasted+10+seconds&page=2)

I'm still working on mine.

I was trying to update openoffice.org when Synaptic told me to repair broken packages first. After doing that, I can no longer logon. Argh . . .

---

