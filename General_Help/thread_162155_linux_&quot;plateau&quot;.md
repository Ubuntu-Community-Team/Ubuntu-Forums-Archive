---
title: "linux &quot;plateau&quot;"
date: 2006-04-18
forum: General Help
---

### Post by chocolatetoothpaste on 2006-04-18
I fear I have reached a plateau with linux.  I love it, but I feel that my growth with it has been stunted.  As linux continues to gain popularity and continues to develop, more and more, tasks are being automated and "simplified" by GUI's.  This is where I feel I have hit a plateau.  I am not satisfied with being a beginner linux user.  I would like to move on to more advanced activities.  Can anyone point me in the right direction?  Books, articles, maybe even another distro I can use on a spare machine (not leaving ubuntu by ANY means)?

---

### Post by tkiesel on 2006-04-18
Hi chocolatetoothpaste,

If you're wanting to dig in and get more in depth with the operating system, I'd say pick an area of interest, get reading and start playing!  One of the great things about Ubuntu is that it's got a nice friendly exterior, while still having the power of Debian inside.

I've learned lots just by experimenting and seeing what I can make the OS do.  I'm typing this to you on a ~6 year old laptop that I've installed Xubuntu on as a test. The school district I work for can save some money by extending the use of machines that choke on Windows XP, but run Ubuntu and derivatives well.

That's been my latest project.  Before that, it was learning to turn Ubuntu into a web server including the famous LAMP stack.  Good times!

I'm still struggling with iPod and digital video editing for a project at work, so there's no shortage of new things to learn.

Not all of these involve digging into the guts of the system's internals, I'll grant you. But that option is there, which is the good thing. (Really digging in with the web server is quite an education!) You can put all of the GUI config helpers in the world on top of Linux, and that's great. If the power of manually configuring the system is still there, then you get the best of both worlds: a system that's newbie friendly and power-user friendly all in one box!

Good luck, and happy exploring!
-T

---

### Post by aysiu on 2006-04-18
Write some shell scripts.

I had a blast writing this one (well, I didn't "write" most of it--most I just stole off the Wiki): [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

In fact, if you need a task, write a good shell script for upgrading from Breezy to Dapper.

---

### Post by chocolatetoothpaste on 2006-04-18
Heck yeah, I would love to write a script for doing that upgrade, but this is where the plateau comes in again, I have no clue what to do, or even where to start.  I am a bit familiar with shell scripting, but I have no idea what to start for an upgrade script.  Any suggestions?

---

### Post by aysiu on 2006-04-18
[QUOTE=chocolatetoothpaste]Heck yeah, I would love to write a script for doing that upgrade, but this is where the plateau comes in again, I have no clue what to do, or even where to start.  I am a bit familiar with shell scripting, but I have no idea what to start for an upgrade script.  Any suggestions?[/QUOTE] Well, I can describe to you what the script *should* do, but I don't really know all that much about shell scripting besides creating one and copying and pasting in some commands.

I know you'll probably need to use the *sed* command to update the sources.list. Maybe someone else can elaborate on other tools you may need.

Here's what the script *should* do:

1. Determine how many desktop environments are installed: XFCE, Gnome, and/or KDE. Install the appropriate metapackage. For example, if someone has XFCE and KDE, the script should recognize that and run ```
sudo apt-get update
sudo apt-get install xubuntu-desktop kubuntu-desktop
``` If someone has only Gnome installed, the script should recognize that and run ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

2. Then, ideally, the script should ask the user whether she would want the X server temporarily stopped during the upgrade, suggesting that this would be a good idea but that it's not a necessary step. If the user says "yes," the script should stop the X server.

3. This is where the *sed* command would come into play (I'm not sure exactly how). The script would have to back up the Breezy list (maybe as /etc/apt/sources_breezy.list) and then replace all instances of the word *breezy* with the word *dapper* and save the sources.list.

4. Finally, the script would do ```
sudo apt-get update
sudo apt-get dist-upgrade
``` and then, if the user asked the X server to be stopped, would restart X.

---

### Post by chocolatetoothpaste on 2006-04-18
All right, I crank on it tonight, and see if I can't have something in time for the release!

---

### Post by aysiu on 2006-04-18
[QUOTE=chocolatetoothpaste]All right, I crank on it tonight, and see if I can't have something in time for the release![/QUOTE] My guess is that if you have questions, you can post your proposed script in the programming section of these forums and get some suggestions from real programmers (i.e., not me).

---

### Post by sxtz on 2006-04-18
try learning a scripting language.  python is a good place to start, i've heard, and i've had good luck so far with learning it.  the first tutorial i tried is located here: [http://www.hetland.org/python/instant-hacking.php](http://www.hetland.org/python/instant-hacking.php) 

it was easy to follow, and the only experience with any language i'd had before was html, css, and mircscript ;)

---

### Post by nanotube on 2006-04-18
hey
you can check out the link in my sig
and go to the section "other command line resources".
i have a few really good links for learning more stuff about linux and commandline, including bash scripting. 
have fun. ;)

---

### Post by openmind on 2006-04-18
As for another distro to play with try 'Archlinux'. I installed it on another box first to play with, and Loved it. Just install the 'Base' to begin with and build a system using 'Pacman' from there. 

You'll spend a lot of time on the command line.;)

---

### Post by sxtz on 2006-04-18
[quote=openmind]You'll spend a lot of time on the command line.;)[/quote]

a lot of time cuz it's always broke, or cuz the command line is just that cool? :p


i'd heard of archlinux but never looked into it..  you mentioned "pacman" so i'm guessing its a package based distro... is it deb or rpm or what?  mostly bin like *buntu or mostly source like gentoo? 

maybe i'll have to check it out... gotta get some DVDs to back up first tho :rolleyes: *ponder,ponder*

---

### Post by openmind on 2006-04-19
[Here's]("http://www.osnews.com/story.php?news_id=5971") a pretty good review from OSNews, you'll be on the command line *exclusively* to begin with as it's up to you to load X, WM, pretty much *everything *(or anything you want) from scratch.

Pacman is a cool manager that supports dependencies pretty much like apt. After re-reading the review I would place less emphasis on the "Expert User" deal, I'm ***far*** from an expert user and I had little problems loading what I wanted. Not one for *complete* Newbies, but a little CLI experience will get you a long way.8)

*Edit: Oh, and a lot of configuring using vi or nano!*

---

### Post by sxtz on 2006-04-19
[quote=openmind][Here's]("http://www.osnews.com/story.php?news_id=5971") a pretty good review from OSNews, you'll be on the command line *exclusively* to begin with as it's up to you to load X, WM, pretty much *everything *(or anything you want) from scratch.[/quote]

awesome! sounds like just what i'm looking for in a second distro to start tinkering with.  thanks for the recommendation, openmind :)

---

