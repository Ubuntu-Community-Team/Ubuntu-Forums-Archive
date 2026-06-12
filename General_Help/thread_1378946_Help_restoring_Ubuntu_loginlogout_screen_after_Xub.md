---
title: "Help restoring Ubuntu login/logout screen after Xubuntu install"
date: 2010-01-12
forum: General Help
---

### Post by WeAreTheSiNs on 2010-01-12
Title pretty much says it all..
anyway i installed Xubuntu desktop and decided i didn't like and uninstalled it.. but it hijacked my boot screen and login/logout screen.
i restored the boot screen but i can't find out how to restore the login/logout screen ](*,)


Any help is greatly appreciated :)

---

### Post by WeAreTheSiNs on 2010-01-12
Bumpity bumpity bump :shock:

---

### Post by lyall on 2010-01-12
> **WeAreTheSiNs said:**
> Title pretty much says it all..
anyway i installed Xubuntu desktop and decided i didn't like and uninstalled it.. but it hijacked my boot screen and login/logout screen.
i restored the boot screen but i can't find out how to restore the login/logout screen ](*,)


Any help is greatly appreciated :)

after you have logon to Xubuntu logoff
at the log on screen click on sessions
at list will show up with all the different GUI to log on
select Gnome and you will log on to that GUI

some like to have the different GUIs 

Good luck and have fun learning

---

### Post by WeAreTheSiNs on 2010-01-12
> **lyall said:**
> after you have logon to Xubuntu logoff
at the log on screen click on sessions
at list will show up with all the different GUI to log on
select Gnome and you will log on to that GUI

some like to have the different GUIs 

Good luck and have fun learning

You misunderstood.. i wasn't talking about sessions.. i mean the actual login screen.. it displays the Xubuntu screen instead of the Ubuntu one..

---

### Post by LegendarySandwich on 2010-01-13
Before I re-installed Ubuntu I had this problem as well. I may wan to to install Xubuntu again, so does anybody have any solutions?

---

### Post by MaxIBoy on 2010-01-13
Try this:
```
sudo dpkg-reconfigure gdm
```

---

### Post by WeAreTheSiNs on 2010-01-13
> **MaxIBoy said:**
> Try this:
```
sudo dpkg-reconfigure gdm
```

About to try it right know :) hope it works

---

### Post by WeAreTheSiNs on 2010-01-13
> **MaxIBoy said:**
> Try this:
```
sudo dpkg-reconfigure gdm
```

Didn't work :(

The only thing different was during boot it had to do a file system check :/ anyway did some more reading up and Karmic appears to not allow you to change it :/

---

### Post by MaxIBoy on 2010-01-13
That's ridiculous, of course it does.

Try this:
```
gksudo gedit /etc/X11/default-display-manager
```
And replace the current line with 
```
/usr/sbin/gdm
```

---

### Post by WeAreTheSiNs on 2010-01-14
> **MaxIBoy said:**
> That's ridiculous, of course it does.

Try this:
```
gksudo gedit /etc/X11/default-display-manager
```
And replace the current line with 
```
/usr/sbin/gdm
```

/usr/sbin/gdm is what is in there already :/

---

### Post by WeAreTheSiNs on 2010-01-15
Edit:
 Wow this was an easy fix... Remove xubuntu-gdm-theme from synaptic and then sudo dpkg-reconfigure gdm and all back to normal..

---

### Post by LegendarySandwich on 2010-01-23
Hmm...how would I do this with Kubuntu? I don't know which file to delete in Synaptic. (By the way, Kubuntu is stilled installed, but I like the Ubuntu starting-up screen better - it's faster.)

---

### Post by WeAreTheSiNs on 2010-01-23
> **LegendarySandwich said:**
> Hmm...how would I do this with Kubuntu? I don't know which file to delete in Synaptic. (By the way, Kubuntu is stilled installed, but I like the Ubuntu starting-up screen better - it's faster.)

Well if both ubuntu and kubuntu desktops are installed just load gnome then delete kubuntu-gdm-theme and it should automaticly reinstall the ubuntu one then sudo dpkg-reconfigure gdm.

---

### Post by LegendarySandwich on 2010-01-23
> **WeAreTheSiNs said:**
> Well if both ubuntu and kubuntu desktops are installed just load gnome then delete kubuntu-gdm-theme and it should automaticly reinstall the ubuntu one then sudo dpkg-reconfigure gdm.
There is no kubuntu-gm-theme, or anything similar.

By the way, it also changed the mouse, and now all the Kubuntu programs are in my Gnome. I was under the impression that the desktops were supposed to be seperate. I guess not :|

---

### Post by WeAreTheSiNs on 2010-01-23
> **LegendarySandwich said:**
> There is no kubuntu-gm-theme, or anything similar.

By the way, it also changed the mouse, and now all the Kubuntu programs are in my Gnome. I was under the impression that the desktops were supposed to be seperate. I guess not :|

lol not not separate (sadly) thats why im dual booting Ubuntu 9.10 and Kubuntu 9.10 :D

hmm maybe sudo apt-get remove kubuntu-gdm-theme and if it doesnt reinstall the ubuntu one sudo apt-get install ubuntu-gdm-theme then do the dpgk reconfigure thing :/ that might work

---

