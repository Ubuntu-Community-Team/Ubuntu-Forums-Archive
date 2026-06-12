---
title: "Need Help Switching to Classic Mode"
date: 2011-09-12
forum: General Help
---

### Post by brendan3863 on 2011-09-12
Hi all,

I just switched to not require a password on login.  The machine can only run classic but the default is set to normal.  When I click the user name, it tries to load normal and crashes and I can't figure out how to make it load classic.  Normally, after you click the user name you can to classic via the bar at the bottom but because it doesn't need a password that option doesn't seem to be available.  Any help is appreciated. 

Thanks!

---

### Post by Splizard on 2011-09-12
_Can you get into a desktop at all?_
If you can then you will be able to run "Login screen", where at the bottom of the application
you can select the default desktop session.

But judging the situation I guess you cant:

_When it crashes can you press Ctrl+Alt+T to bring up a terminal?_
If you can, type in:
```
gdmsetup
```this will bring up the "Login screen" application.

I hope that will help!

If that does not work you will have to find a way to do it via the command-line interface...
(Not my best area) ;)

---

### Post by 3rdalbum on 2011-09-12
The file ~/.dmrc (which is a hidden file called ".dmrc" inside your home directory) controls what session is used when you log in. You can modify this file in the terminal.

This is what's in my .dmrc file:

```
[Desktop]
Session=ubuntu
Language=en_US.utf8
Layout=us
Langlist=en_US:en
LCMess=en_US.UTF-8
```

I use the default Ubuntu (Unity 3D) session on this computer, which is why "ubuntu" is set in the Session line. You need to modify this to what phillinux has posted underneath this message.

Basically, to actually make the modification, you need to press Control-Alt-F1 to get to the text terminal. Log into this text terminal, then type the following to start editing the appropriate file:

```
nano .dmrc
```

Change the Session line so it reads:

```
Session=gnome-classic
```

and then press Control-X, then the Y key, then Enter. (this tells the editor to exit, that you want to save changes, and then Enter to confirm the file name). Then put the following into the terminal:

```
sudo service gdm restart
```

which will restart the login screen and you should now be able to click on your username and go straight to the session you made the modification for.

EDIT: Thanks phillinux for telling us what to change the file to :-)

I'll just finish by being preachy and telling you that it's a bad idea to slacken the security on your computer. You're a grownup and it's your computer, so do what you please, but it would be remiss of me not to recommend restoring the login password.

Reference: [http://library.gnome.org/admin/gdm/stable/configuration.html.en#userconfig](http://library.gnome.org/admin/gdm/stable/configuration.html.en#userconfig)

---

### Post by philinux on 2011-09-12
This is my file contents for gnome classic.

```
cat ~/.dmrc
```

```
[Desktop]
Language=en_GB
Layout=gb
Langlist=en_GB:en
LCMess=en_GB.UTF-8
Session=gnome-classic

```

---

### Post by brendan3863 on 2011-09-12
Opening the terminal and using ```
gdmsetup 
``` allowed me to switch to classic mode.  I then needed to enter ```
sudo chmod 755 /etc/gconf/gconf.xml.system
``` from this thread  [http://ubuntuforums.org/showthread.php?t=917306]("http://ubuntuforums.org/showthread.php?t=917306") and that seems to have solved my problems.  Thank you all for the help.

---

