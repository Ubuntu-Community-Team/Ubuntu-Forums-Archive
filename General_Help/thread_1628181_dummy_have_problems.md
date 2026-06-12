---
title: "dummy have problems"
date: 2010-11-22
forum: General Help
---

### Post by freefixkorma on 2010-11-22
hi guys what are the most important things to do after installing ubuntu 10.10 netbook edition on my acer i am doing a fresh install ,in my previous install i really had trouble with the panels how can i improve that i mean like just regular panel like in 10.4 that where on top , i will appreciate any help and how to setup after a fresh install i will appreciate any guidance thanks in advance

---

### Post by aromo on 2010-11-22
This is a reduced list of things I did right after I installed Maverick on my laptop and my wife's:

1. Set up wireless network
2. Change root password: <snip>
9. Find the fastest repository: Applications > Ubuntu Software Centre > Edit > Software Sources... > Download from: Other... > Select Best Server
10. Enable partner repository
11. sudo apt-get update
12. Install BleedingEdge ([http://sourceforge.net/projects/bleedingedge/](http://sourceforge.net/projects/bleedingedge/)), and install:
    Additional repositories
    Flash Player
    Google Chrome
    Restricted extras & codecs
    Sun Java 6
    VLC media player
    Wine
13. Install other applications:
    7zip => Archiver
    K9copy => DVD ripper
    gBrainy => Game
    DeVeDe => DVD authoring
    Pitivi Video Editor
    CD Juicer => CD ripper

After having done this, you're pretty much good to go.  Hope it helps!

---

### Post by uRock on 2010-11-22
> **aromo said:**
> This is a reduced list of things I did right after I installed Maverick on my laptop and my wife's:

1. Set up wireless network
9. Find the fastest repository: Applications > Ubuntu Software Center > Edit > Software Sources... > Download from: Other... > Select Best Server
11. sudo apt-get update
12. Install:
    Additional repositories
    Restricted extras & codecs
    VLC media player
    
After having done this, you're pretty much good to go.  Hope it helps!

Removed all of the stuff that is not likely to be used on a Netbook.

---

### Post by Megaptera on 2010-11-22
A blog on that subject here:

[http://breakthebit.org/post/564380600/pimp-my-linux-ubuntu-10-04](http://breakthebit.org/post/564380600/pimp-my-linux-ubuntu-10-04)

"This tutorial is targeted at netbook users, that want to streamline and tweak their Linux. Though it&#8217;s perfectly suitable for other people, provided they have the necessary knowledge. It has been tested on and meant mainly for the new Ubuntu 10.04 release on an ASUS eeePC 1005PE and a Lenovo S10-2, both running the RC version.
Be careful with what you are doing, and you&#8217;ll be fine. Use information here at your own risk."

---

### Post by freefixkorma on 2010-11-23
guys i am having trouble with touchpad it always screw me when i writing anything i can do to disable the touch pad i will appreciate ,i am running on ubuntu 10.10 netbook edition thanks in advance for the help

---

### Post by Megaptera on 2010-11-25
Try going to Control Centre > Mouse and to third tab and "disable touchpad while typing"

Hope that works?

---

### Post by Megaptera on 2010-11-27
Or, just found this today ...

[http://www.webupd8.org/2010/11/touchpad-indicator-lets-you-quickly.html](http://www.webupd8.org/2010/11/touchpad-indicator-lets-you-quickly.html)

"Touchpad Indicator is a very simple indicator created by Lorenzo Carbonell (the Picapy developer), which as the name suggests, is designed to allow you to easily enable / disable your laptop or netbook touchpad."

---

