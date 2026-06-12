---
title: "Autostart lirc at startup"
date: 2005-02-09
forum: General Help
---

### Post by Titeuf on 2005-02-09
I've succesfully downloaded and installed lirc 0.7 (I did not use the 0.6 that was in the repositories, because I never could make those work before)
But now I have a question: how can I automatically start lircd when ubuntu boots ?

---

### Post by Wim Sturkenboom on 2005-02-10
I suppose you want that when you login into the GUI (which is not the same as when Ubuntu boots).

Menu *Computer->Desktop Preferences->Sessions*, tab *Startup Programs*.

---

### Post by Titeuf on 2005-02-10
[QUOTE=Wim Sturkenboom]I suppose you want that when you login into the GUI (which is not the same as when Ubuntu boots).

Menu *Computer->Desktop Preferences->Sessions*, tab *Startup Programs*.[/QUOTE]
No, I want lircd to be loaded before gdm, and it has to be started as root.
This can't help me

---

### Post by Wim Sturkenboom on 2005-02-10
Sorry, did not know that it was a server/daemon.

Add a symbolic link in one of the directories *rcX.d* where X is a number or letter. These directories are located in the */etc* directory.
Which one it will be, is determined by the runlevel that is used when Ubuntu boots. This can be found in the file */etc/inittab*. There is a line like:```
id:2:initdefault
```This says that Ubuntu is booted into runlevel 2. For that reason the symbolic link has to be in *rc2.d*
Check your system; it will probably also be 2.

A symbolic link can be created with ```
ln -s app dest
```Execute this command in the rc2.d directory (or whichever one it was). *app* is the executable (including its full path), *dest* is the name of the link; S98lirc will probably be a good name.

The applications are loaded in alphanumerical order. So something starting with S10 will be loaded before something starting with S44.
The *S* indicates start. Leave it in so it does not confuse you later on.
Have a look at rc6.d; scripts there are executed on shutdown. This contains links with a *K* (for kill).

Last but not least. Usually the links in the rcX.d directories point to scripts in the */etc/init.d* directory. To really make it nice, you should make a script in that directory that starts lirc. Advantage is that you can also pass parameters (in the script). Next let the symbolic link point to the script.

---

### Post by Titeuf on 2005-02-10
Thank you very much :-)

---

### Post by knathraak on 2005-03-30
If you have already set up lirc, it is surprising that there aren't rc scripts already set up in your rcX.d directories.  But if there aren't, a more elegent solution than manually linking to /etc/init.d/scriptname is to use the update-rc.d utility.  It lets you specify the init.d/script and desired runlevels as arguments.

However be warned, if there isn't already a /etc/init.d/lirc script, then something has gone wrong in your setup of lirc.  The lirc init script is moderately complex and does several things.  (1) it starts two different daemons, lircd and lircmd.  (2) it reads in /etc/lirc/hardware.conf to get parameters to pass to the daemons such as what devices to use, what modules to load, and what arguments to pass to the commands, etc. (3) provides several case statements for different arguments to the init script such as [start|stop|restart|reload|etc].  So if you don't already have that script, it is non-trivial to create it from scratch.

If there are already rc scripts set up, then it could be that the daemon is trying to start at boot, but is dying.  In my case my configuration was somewhat borked, and I had to adjust things manually in hardware.conf (pointing to the wrong lirc device, in my case).

Good luck

---

### Post by Haegin on 2005-10-28
why is lirc so hard to setup and get working? Is there a GUI anywhere that I can use?

Thanks

---

