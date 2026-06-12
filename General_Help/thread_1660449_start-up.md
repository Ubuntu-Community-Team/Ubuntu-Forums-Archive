---
title: "start-up"
date: 2011-01-05
forum: General Help
---

### Post by rahulnair on 2011-01-05
hi guys..i was trying to add a script to start-up in ubuntu 10.04..but no luck so far..

actually had read somewhere that..you have to add your script to the /etc/profile.d/ folder so that  the /etc/profile executes all scripts in the profile.d directory while logging in..
but i still cant get it working..
am i doing it correct?

---

### Post by seawolf167 on 2011-01-05
This should help

[UbuntuBootupHowto]("https://help.ubuntu.com/community/UbuntuBootupHowto")

---

### Post by Verbeck on 2011-01-05
try adding a line to /etc/rc.local 
eg;
```
/bin/sh /path/to/your/script.sh
```*give the script execute permission first

---

### Post by lithopsian on 2011-01-05
Putting a script in /etc/profile.d is usually a good way to get it executed at "startup".  Strictly, where you put scripts depends on your desktop environment but I'll assume that is just standard Gnome.  Window managers will also have their own ways to run startup scripts and programs.  Openbox has an autostart.sh, although you probably have Metacity.  There is also a simple startup menu where you can add applications to be run at startup.

What happens for you?  Or doesn't happen?

---

### Post by lithopsian on 2011-01-05
Hmmm.  I hadn't considered that you might actually be wanting to add a script to the boot process.  That isn't something that you would generally be doing, but is certainly possible as described.  rc.local is the preferred place to put your own customisations.  Try to stay out of rcS.d and the rcN.d numbered directories, but if you have to then entries should be symlinks to a script in init.d.  Each login will execute the symlinks in rcS.d and also the ones in the rcN.d directory for your runlevel (including rc0.d and rc6.d for shutdown and reboot).  These are for things that you want to run every time you boot, X session or command line, to be run as root, things like daemons and hardware configuration.

Inside Gnome or Metacity will be applications that you run as the logged in user, and obviously only during Gnome sessions.

---

### Post by rahulnair on 2011-01-05
wow..thanks guys for helping me..


> Putting a script in /etc/profile.d is usually a good way to get it executed at "startup"yeah i tried doing that the first time but it just wont run...dont know why.
but now while waiting for replies , i happened to find out a method from some online article..

but i am not sure , if it is the correct way to do it...(i am new to linux) .
what i did was

1.to add the script to init.d folder
2.run the command    sudo update-rc.d -f cleand.sh start 99 2 .
and it seems to work now....

is this the correct method to do it??

---

### Post by seawolf167 on 2011-01-05
> **rahulnair said:**
> 
1.to add the script to init.d folder
2.run the command    sudo update-rc.d -f cleand.sh start 99 2 .
and it seems to work now....

is this the correct method to do it??

The "correct" method according to the community documentation can be found in the link I posted previously

---

### Post by rahulnair on 2011-01-05
ok....thanks again seawolf...:p..that was almost the same what i did..:KS..
marking solved...

---

