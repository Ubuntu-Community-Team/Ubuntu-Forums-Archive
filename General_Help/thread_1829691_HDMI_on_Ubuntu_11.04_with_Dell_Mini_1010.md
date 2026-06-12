---
title: "HDMI on Ubuntu 11.04 with Dell Mini 1010"
date: 2011-08-20
forum: General Help
---

### Post by LMartin87 on 2011-08-20
Hey there,

I have a Dell Mini 1010 (came with windows) that i have installed Ubuntu 11.04 on.

I had to update the graphic drivers to the EMGD to get video to work and not be jumpy and it also gave me more options of resolution.

The problem i have is that HDMI out wont work at all. When plugged into my TV it wont pick it up as a second monitor.


xrandr gives me:
[http://i51.tinypic.com/5o8h13.jpg](http://i51.tinypic.com/5o8h13.jpg) 


Monitor settings shows:
[http://i53.tinypic.com/mhgdon.jpg](http://i53.tinypic.com/mhgdon.jpg)

Any idea what i can do?

---

### Post by vickoxy on 2011-08-21
Did you try to use it with some other external display? I have no solution for you, but am interested in this issue.

---

### Post by LMartin87 on 2011-08-21
> **vickoxy said:**
> Did you try to use it with some other external display? I have no solution for you, but am interested in this issue.

Ive tried it on two differant TVs, the Dell Mini 1010 only has HDMI out no VGA. 

The HDMI out works fine on Windows and JoliOS

---

### Post by LMartin87 on 2011-08-22
Is this in the right section to get some help??

---

### Post by vickoxy on 2011-08-23
Did you try to install this driver:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

HDMI should work with some tweaking without problems:
[http://forum.ubuntuusers.de/topic/schnittstellen-und-monitorerkennung/#post-3269007](http://forum.ubuntuusers.de/topic/schnittstellen-und-monitorerkennung/#post-3269007)

Sorry, in your first post stays you did. So try:
```
wget http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo.sh && sh ./poulsbo.sh
```

And after restart
dpkg-reconfigure psb-kernel-source

---

### Post by LMartin87 on 2011-08-23
> **vickoxy said:**
> Did you try to install this driver:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

HDMI should work with some tweaking without problems:
[http://forum.ubuntuusers.de/topic/schnittstellen-und-monitorerkennung/#post-3269007](http://forum.ubuntuusers.de/topic/schnittstellen-und-monitorerkennung/#post-3269007)

Sorry, in your first post stays you did. So try:
```
wget http://dl.dropbox.com/u/1338581/Gma500/scripts/poulsbo.sh && sh ./poulsbo.sh
```And after restart
dpkg-reconfigure psb-kernel-source

After typing this in terminal i get a 404 not found error

---

### Post by vickoxy on 2011-08-24
Well, for Natty stays:

```
sudo add-apt-repository ppa:gma500/emgd 
sudo apt-get update
sudo apt-get install xorg-emgd emgd-dkms emgd-xorg-conf
sudo emgd-xorg-conf
```

I presume you made all that?

EDIT: it semems that 10.10 worked best here:
[http://ubuntuforums.org/showthread.php?t=1746934](http://ubuntuforums.org/showthread.php?t=1746934)
don´t know if 11.04 is fixede. Maybe you should try 10.10?

---

### Post by LMartin87 on 2011-08-24
> **vickoxy said:**
> Well, for Natty stays:

```
sudo add-apt-repository ppa:gma500/emgd 
sudo apt-get update
sudo apt-get install xorg-emgd emgd-dkms emgd-xorg-conf
sudo emgd-xorg-conf
```I presume you made all that?

EDIT: it semems that 10.10 worked best here:
[http://ubuntuforums.org/showthread.php?t=1746934](http://ubuntuforums.org/showthread.php?t=1746934)
don´t know if 11.04 is fixede. Maybe you should try 10.10?

Yeah that code above is what i used to upgrade the graphics drivers that allowed be to change the resolution of my netbook screen, but it still wont pick up external monitors via HDMI

---

### Post by atomicx6637 on 2011-08-26
I'm having the same problem.  Did you get a resolution to this?

---

### Post by LMartin87 on 2011-08-27
> **atomicx6637 said:**
> I'm having the same problem.  Did you get a resolution to this?

No ive not managed to find one yet :(

Theres only a few people on here that seem to be able to help.

---

### Post by pgpoulsen on 2011-08-28
I have the same problem, just that mine is a Asrock 152D with NVidia ION graphics chip.

Wish there was some solution out there :-(

Yours
/peter

---

