---
title: "no gksudo gedit /etc/X11/xorg.conf"
date: 2009-10-24
forum: General Help
---

### Post by dbyjazz on 2009-10-24
Hi guys,

I'm using the Ubuntu 9.10 beta and I need to change something in my gksudo gedit /etc/X11/xorg.conf file and it doesn't appear to even exist. More specifically there's nothing in it.

---

### Post by dbyjazz on 2009-10-24
this is what I'm trying to do because I have to change my screen resolution manually.

```
Subsection "Display"
    Depth 24
    Modes "1280x768"
    Virtual 1280 768
EndSubsection
```

and at the moment it's set as 1600x1200 so everything goes off the screen

---

### Post by Johnny B on 2009-10-24
did you try:
> dpkg-reconfigure xserver-xorg

---

### Post by dbyjazz on 2009-10-24
I'm trying to download root but it won't let me for some reason

```
derek@derek-laptop:~$ sudo apt-get install root-system-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  root-system-bin: Depends: libroot5.18 (>= 5.18.00) but it is not going to be installed
                   Depends: root-plugin-asimage but it is not going to be installed
                   Recommends: root-plugin-gl but it is not going to be installed
                   Recommends: libroot-minuit or
                               root-fitter
                   Recommends: libroot-dev but it is not going to be installed
E: Broken packages
derek@derek-laptop:~$ 

```

---

### Post by 3rdalbum on 2009-10-24
Did you put the capital X in X11 when you were typing that command? Linux is case-sensitive.

---

### Post by dbyjazz on 2009-10-24
> **3rdalbum said:**
> Did you put the capital X in X11 when you were typing that command? Linux is case-sensitive.

yeah I checked that as well

edit; installing root right now

---

### Post by 3rdalbum on 2009-10-24
> **dbyjazz said:**
> I'm trying to download root but it won't let me for some reason

```
derek@derek-laptop:~$ sudo apt-get install root-system-bin

```

Root-system-bin is something different entirely; it doesn't have anything to do with the root account on Linux. Don't install this package unless you want to do numerical analysis.

What happens if you paste in this command:

```
cat /etc/X11/xorg.conf
```

Have you tried getting Ubuntu to re-create a standard xorg.conf through this command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by dbyjazz on 2009-10-24
> **3rdalbum said:**
> Root-system-bin is something different entirely; it doesn't have anything to do with the root account on Linux. Don't install this package unless you want to do numerical analysis.

What happens if you paste in this command:

```
cat /etc/X11/xorg.conf
```

```
cat: /etc/X11/xorg.conf: No such file or directory
```

---

### Post by sgosnell on 2009-10-24
So create it with the commands given above, then edit it.

BTW, it's not a "gksudo gedit /etc/X11/xorg.conf" file.  Gksudo is a command to run a graphical interface app as superuser.  Gedit is the standard Gnome text editor.  The filename is xorg.conf, and it's in the /etc/X11 directory.  You may know this, and I'm not trying to insult you, but your initial post wasn't clear to me about that.

---

### Post by dbyjazz on 2009-10-24
> **sgosnell said:**
> So create it with the commands given above, then edit it.

BTW, it's not a "gksudo gedit /etc/X11/xorg.conf" file.  Gksudo is a command to run a graphical interface app as superuser.  Gedit is the standard Gnome text editor.  The filename is xorg.conf, and it's in the /etc/X11 directory.  You may know this, and I'm not trying to insult you, but your initial post wasn't clear to me about that.

yeah sorry I noticed that after I posted it ha

it won't create the file though. The editor opens and it's completely blank

this is what I'm doing

```
derek@derek-laptop:~$ sudo dpkg-reconfigure xserver-xorg
derek@derek-laptop:~$ 
```

so basically it just goes back to 'derek@derek-laptop:~$' after I type it in.

---

### Post by ranch hand on 2009-10-24
I would not create the file.  9.10 comes with out it by default.  If you configure something it will be there.  It may hose your system if you create it and just configure it as some earlier version was configured.

The karmic testing forum would be a better place to post this kind of question, as folks there know the issues.
[http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)

---

### Post by dbyjazz on 2009-10-25
thanks bro

---

### Post by sgosnell on 2009-10-25
The 2.6.31 kernel won't do the increased resolution anyway.  It works fine with 2.6.30 and earlier kernels, but not in Karmic.  You're wasting your time at this point.  Updated kernels might work eventually, but not now.

---

