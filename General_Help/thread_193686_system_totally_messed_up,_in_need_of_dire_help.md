---
title: "system totally messed up, in need of dire help"
date: 2006-06-10
forum: General Help
---

### Post by truenemesis on 2006-06-10
hello,
i got three major issues.

first off, I cant view https sites with Firefox. Im missing a package called nss3. Actually, aptitude is telling me its broken. And synaptic cant find it anywhere and cant fix it. Any idea how to fix this? Maybe I should switch to the original source.list? Does anyone have a copy of the original dapper souce.list?

None of my gnome-panel applets are working anymore. When everything boots up, I get an error message. 

The panel encountered a problem while loading "OAFIID:GNOME_ClockApplet".
Do you want to delete the applet from your configuration?

I tried to reinstall gnome-panel. I get dependency problems with the gnome-panel packages.

And finally, I cant play any music. I keep getting internal data flow error. I uninstalled all gstreamer 8 files and only have gstreamer 10 files. 


SOMEONE PLEASE HELP ME.

---

### Post by truenemesis on 2006-06-10
im also missing a file called libgstcontroller when I try to use listen player. And I cant find this package anywhere on the net.

---

### Post by blackjack6.21.91 on 2006-06-10
Alright.  So it seems like your missing a whole lot of necessary packages to do *very* basic things.  Here's my sources.list

> deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


I would recommend reinstalling gnome-desktop (or kde-desktop) and all of your broken packages.  I hope that helps

---

### Post by truenemesis on 2006-06-10
how would I go about reinstalling ubuntu-desktop? WIll it mess up everything when I mark it for reinstallation?

---

### Post by Skye on 2006-06-10
truenemisis, this is what you need to do:

Open up a terminal, and run ```
sudo gedit /etc/apt/sources.list
``` when gedit opens up, delete everything in the file.  Once you've done that, copy and paste the contents of the file that blackjack6.21.91 posted for you.  Save it, and close gedit.

Once you've done that, do this:
```
sudo apt-get update
sudo apt-get upgrade
```

If it asks you to install anything new, let it.  Once that finishes running, do this:
```
sudo apt-get install --reinstall ubuntu-desktop
```

Once all that is done, reboot, and see if things are better.  

It sounds like you upgraded from Breezy, and either stopped halfway through, or the installation process broke somehow.  Ubuntu-Desktop is what's called a "metapackage" that installs all the necessary programs to have a functioning Ubuntu desktop machine- it doesn't actually have any data associated with it, but installing it again will make sure that everything necessary is installed.

Good luck!

EDIT: Fixed typo.
EDIT2: Thanks, Ramses- fixed that typo too.

---

### Post by Ramses de Norre on 2006-06-10
[QUOTE=Skye]
```
sudo apt-get install --Reinstall ubuntu-desktop
```
[/QUOTE]
It should be **r**einstall =) 

EDIT: I'm sorry, I see yours works too.

---

