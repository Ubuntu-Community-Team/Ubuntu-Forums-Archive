---
title: "Xserver issue"
date: 2010-05-03
forum: General Help
---

### Post by lemmy999 on 2010-05-03
Having done a clean re-install of 10.4 I am now experiencing major problems. I cannot log in to the PC using the usual GUI. On login the machine drops to terminal. I can log in but when I try "startx" I get the following error message
```
fatal server error
no screens found

ddxSigGiveUp: closing log

xinit: no such file or directory (errno2) unable to connect to xserver
xinit: no such process (errno3): server error
```

Try to get a look at the log file gets me the following
```
gedit:1304; Gtk-Warning** cannot open display
```
How do i go about getting xserver back up and running?

OK- got it fixed
1. removed the old xorg.conf
[CODE]sudo rm -f /etc/X11/xorg.conf /CODE]
2. removed all the old nvidia drivers
[CODE]sudo apt-get --purge remove nvidia-*/CODE]
3. re-installed the official nvidia drivers from the repos
[CODE]sudo apt-get install install nvidia-current, nvidia-current-modaliases, nvidia-common/CODE]

Reboot!

Big sigh of relief!! I won't be going anywhere near the closed source nv drivers for a while yet!!

---

### Post by utnubuuser on 2010-05-03
Don't know the solution to your problem, but you might want to post some system info, such as the output of > sudo lspci -lWhat kind of video card if any.

It's probably as easy as enabling a driver,  or setting up a xorg.conf file.

It used to be > sudo dpkg-reconfigure xserver-xorgbut I'm thinking that command has changed.

If you've done a clean install, there should be no xorg.conf file in /etc/X11, and you'll have to create one.
I "think" the new command is > sudo Xorg-configurebut I'm not sure.
You could just make a xorg.conf file in /etc/X11 then run > sudo dpkg-reconfigure xorg.conf -phigh to see where that gets you.  It wont hurt anything, and if it doesn't work, you can remove the file through the command line.

If you've got a nVidea card or other video card, the procedure is different.

---

### Post by lemmy999 on 2010-05-03
@utnubuuser

Its definitely an Nvidia card. On logging out i got a message about the machine dropping to "low graphics" mode. On reboot there's no xserver at all.

I tried lspci -l but get too much detail so i cannot pull the relevant bits out.

I also tried "sudo X-org-configure" but get the reply " command not found"

---

### Post by lemmy999 on 2010-05-03
OK- got it fixed
1. removed the old xorg.conf
```
sudo rm -f /etc/X11/xorg.conf 
```
2. removed all the old nvidia drivers
```
sudo apt-get --purge remove nvidia-*
```
3. re-installed the official nvidia drivers from the repos
```
sudo apt-get install install nvidia-current, nvidia-current-modaliases, nvidia-common
```

Reboot!

Big sigh of relief!! I won't be going anywhere near the closed source nv drivers for a while yet!!

---

### Post by kouter on 2010-05-03
```
Xorg -configure
mv xorg.conf.new /etc/X11/xorg.conf
sudo aptitude reinstall nvidia-current
```

probably a little neater workaround

---

