---
title: "should i  remove xubuntu or not?"
date: 2011-10-26
forum: General Help
---

### Post by techvish81 on 2011-10-26
I installed xubuntu on my ubuntu installation  from an alternate ISO and then to revert back to Ubuntu , I installed Ubuntu desktop from the repos, now I want to know,  can I remove xubuntu desktop and things related to it or it will break my system?

---

### Post by linuxwin2 on 2011-10-26
```

sudo apt-get autoremove xubuntu-desktop xfce

```

---

### Post by ajgreeny on 2011-10-26
This page may help, but make sure you use the right page for yopur version of Ubuntu/Xubuntu.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by techvish81 on 2011-10-26
> **ajgreeny said:**
> This page may help, but make sure you use the right page for yopur version of Ubuntu/Xubuntu.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

actually my situation is a bit complicated then in the thread.  

when I boot , get xubuntu splash screen and xubuntu login,  but I login to unity using xubuntu login. so the os  installed is xubuntu and Ubuntu desktop is installed as additional desktop from the repo,  
now I want to stay in Ubuntu,  so xubuntu is actually useless for me. so is it advisable to remove xubuntu or will it break system to the point,  where I will not be able to boot.?
first reply gave no results,  obviously because it is basically a xubuntu . second reply is for a different case. 

still thanks for replying.

---

### Post by techvish81 on 2011-10-26
bump

---

### Post by techvish81 on 2011-10-26
bump

---

### Post by scania_gti on 2011-10-26
Try reinstall ubuntu from CD. In my case - i boot my xubuntu with kubuntu splash screen, ad boot was slow... Tried remove kubuntu in few ways with no luck.
Then reinstall xubuntu from CD, and boot starts run normaly.

---

### Post by ajgreeny on 2011-10-26
There is no reason why that long command I gave you from psychocats shoudl break your system, as you also have ubuntu-desktop package installed and the packages that are needed for that, but which are also in the xfce desktop will not be removed if they are dependencies of ubuntu-desktop.

To check what it will do use the -s option for the apt-get command
> -s, --simulate, --just-print, --dry-run, --recon, --no-act
           No action; perform a simulation of events that would occur but do not actually change the system. Configuration Item: APT::Get::Simulate.is from man apt-get and tells you what it means.

---

### Post by oldtimer7777 on 2011-10-26
I've tried that Psychocats command line uninstallation of xubuntu, and I will tell you from first hand experience that it is better to just reinstall from a fresh copy of the latest Ubuntu and clean it out that way.  If you just installed xubuntu, then you don't have to worry about data loss from wiping that partition either. If you do it from a Flash Thumb Drive to install Ubuntu, it will take about the same amount of time on a newer computer. It only take about 10-15 minutes tops from a Flash Drive Live installation of Ubuntu..  Just my two cents. :KS

> **ajgreeny said:**
> There is no reason why that long command I gave you from psychocats shoudl break your system, as you also have ubuntu-desktop package installed and the packages that are needed for that, but which are also in the xfce desktop will not be removed if they are dependencies of ubuntu-desktop.

To check what it will do use the -s option for the apt-get command
is from man apt-get and tells you what it means.

---

### Post by techvish81 on 2011-10-27
thank u all , I did a fresh install of Ubuntu.  
to avoid all the possibilities.

---

