---
title: "Restoring Removed Packages From History"
date: 2012-09-13
forum: General Help
---

### Post by Mad-Halfling on 2012-09-13
I will start off by saying I WAS STUPID - I did this during my work lunchtime so I was under time constraints and so didn't spend as much time and care as I should have done :)

I was running 11.10 with Gnome3 and I fancied trying out Unity again (as there's been a lot of work done on it), plus I thought I would upgrade to 12.04.  I ran the 12.04 distro upgrade first, figuring it *might* revert to Unity, but it didn't, so I found some instructions on reverting and started to follow them (it was one of these sets [http://supportlife.wordpress.com/2011/05/31/tutorial-how-to-removeuninstall-gnome-3-in-ubuntu-11-04-natty-narwhal/](http://supportlife.wordpress.com/2011/05/31/tutorial-how-to-removeuninstall-gnome-3-in-ubuntu-11-04-natty-narwhal/) ).  However the ppa-purge didn't work - it couldn't find the PPA to remove, for some reason: I suspect it may have been due to the fact that it was the old Ubuntu version's one - but stupidly/valiantly I soldiered on.  It didn't work and so I ended up manually removing the old Gnome 3 PPA files and adding the Precise Gnome 3 PPAs - then I managed to get Gnome 3 back up and running.  Unfortunately the process had already removed a *shedload* of packages, which I would like to get reinstalled until I can sit down properly and look at getting Unity back.  I can find the list of removed packages in the Software Centre and in /var/log/apt/history.log but I can't find a way to reinstall them en masse (there are quite a few of them, so it's quite painful to have to find them all in Synaptic or apt-get install them).  Is there a way of doing this, easily, or do I have to pay for my foolishness with some time at the command line?
Thx - MH

---

### Post by Bashing-om on 2012-09-13
Mad-Halfling; Hi !

It is doable. However, I am confused as to what you desire for an end result.
  a. Your DE as unity only ?
  b. Do you want both unity and gnome3.4 available ? 

In any case, clean up the package information thus:
```

sudo apt-get clean
sudo rm /var/lib/apt/lists/*
sudo rm /var/lib/apt/lists/partial/*
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
sudo apt-get clean
sudo apt-get update

```Now lets see if unity re-installs:
```

sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity

```This should get your desk top back. If all is good at this point and you also want gnome we will proceed to install gnome also. 
  Else: In the event of problems, Post back with the exact errors generated.[INDENT]kind regards <==BDQ
[/INDENT]

---

### Post by Mad-Halfling on 2012-09-18
Small steps:-
To start off with, I just want to be able to restore the packages that were removed as part of my attempt to revert to Unity.  This list is sitting in my log, as I mentioned, but is quite substantial to do manually.

Once I've done this, I can sit down and look at reverting to Unity but I want to get my packages back until I have time to sit down and (properly) see what the problem was with reverting - I can't remember, exactly, what the problem was, but it couldn't purge the Gnome 3 PPA properly, IIRC.  However, step 1 is what I want to do first so that if I have the problem again, I can still get back to where I was.

Cheers - MH

---

### Post by Bashing-om on 2012-09-18
I am a one-step-at-a-time guy myself.

the first block of codes (one command at a time) will regenerate the config files, and updates the files. If that goes well ..then comes up date all system packages.

[INDENT]kind regards <==BDQ

[/INDENT]

---

### Post by Mad-Halfling on 2012-09-21
Thanks - I understand (or, at least, I think I do - please correct me if I'm wrong) what those commands are doing (a full reset of the software sources, then a reinstall of the vanilla package list), but as I won't have a decent chunk of time to sit down and do that properly (just in case something goes wrong) for a few weeks I was hoping to get my system back to the state it was in before I started, that fateful day (I keep finding functions that are missing and then have to go and reinstall the missing packages individually, so I was thinking it's better to get everything back, in one fell swoop, if I can).
I've found (and created a labelled copy of) the (/var/log/apt/)apt log file which recorded the package removals, and I can see them in the Software Centre's log, too but there seems to be no way of getting these installed again.  A section of the /var log is:-

Commandline: apt-get remove libgtk-3-common
Install: polkit-kde-1:amd64 (0.99.0-3ubuntu5, automatic)
Remove: imgizor:amd64 (0.5~ppa4-0~17~oneiric1), ubuntu-artwork:amd64 (57), gnome
-shell-extensions-xrandr-indicator:amd64 (3.2.0-2~webupd8~oneiric), gnome-sessio
n-canberra:amd64 (0.28-3ubuntu3), xdg-user-dirs-gtk:amd64 (0.9-0ubuntu1), ubuntu
-desktop:amd64 (1.267), gnome-power-manager:amd64 (3.4.0-0ubuntu1), libido3-0.1-
0:amd64 (0.3.4-0ubuntu1), unity:amd64 (5.14.0-0ubuntu1), indicator-printers:amd6
4 (0.1.6-0ubuntu1), nautilus-search:amd64 (0.9-0~9~oneiric1), libevolution:amd64
 (3.2.3-0ubuntu6),......

- is there a way of easily installing all the listed packages that were removed, again?  I was thinking of possibly processing it with sed or awk to extract the package names, but again it's the time factor, plus I'm surprised there isn't an easier way to do this (me missing something basic, is a possibility).
This is also a bit of a general question, as it is specific to my current circumstances, for my own reference - I'm sure this happens relatively often on a smaller scale.

Thanks for what you listed above - it's most useful and I will give it a go when I can - but I'm in the classic situation: IT people never have the time to work on their own systems, haha, and my GF will not be happy if my laptop isn't working for her to play WoW on!

---

### Post by Bashing-om on 2012-09-21
Mad-Halfling;
  Not to say installing the packages one at a time will not work ...it will ! ..But will be time consuming to identify dependencies as you install // and then you find that one package that supports another should have been installed prior ...

  ok ..ubuntu package management is smart ...real smart. What we are going to do with the 1st block of code is to move the "bad" source files out of the way, regenerate new ones, The package manager will compare what is on the system to what is available in the repository (apt-get update). For the indepth documentation:
[https://help.ubuntu.com/11.04/serverguide/package-management.html](https://help.ubuntu.com/11.04/serverguide/package-management.html)

Then tell us what is going on and any problems it need help with. We look it over to be aware.
Tell the system to get the packages it needs to be up to date (apt-get upgrade).
finally, we will insure no mess is left behind with a couple of clean up commands.

Hopefully it is that easy and done.

off topic: Know what you are saying about getting time to work on your own stuff--- cobbler's kids do not have shoes--// In this case you having been fighting problems all day ..come home and have to have a different mind-set to cope with linux. Bear in mind that linux has been around since day 1; literally millions of programmers have developed an awesome system and the tools have evolved to work within linux.

[INDENT]high regards <==BDQ
[/INDENT]

---

### Post by Mad-Halfling on 2012-09-23
Yup, this is my current problem - putting the reverting to Unity aside, I want to get my system back to the state it was in with Gnome 3: I know I could individually install all the packages but there's an absolute shedload of them - and, of course, if I had time to do that, I'd have time to sort out going back to Unity.  Hence my wondering if there's a way to reverse the package removal in one go, or at least strip the non-package name information from the log file so I could do one monstrous apt-get install to get them back.  I'm surprised there isn't a way to do this, easily, as I'm sure I'm not the first person to want to do this?

---

