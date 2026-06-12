---
title: "Thank God for Ubuntu"
date: 2006-05-26
forum: General Help
---

### Post by litho23 on 2006-05-26
Here is a brightfully cheering story that this distribution is doing something right.

Once upon a time, (about 2 years ago)  I started to dibby dable with linux I started with Red Hat, (wasn't for me and didn't work with my hardware too well. I tend to have a curse of forking over my weekly paycheck to get the latest hardware) . I tried a few more, but didn't find anything to my liking, so back to Windows I went.

(many many days and nights later)
Couple weeks ago after getting really really bored of windows and angry at Microsoft for ruthlessly forcing me have to buy an XBO360, just so I can play Halo3 this November. Not to mention at the same time I already planned to acquire a Playstation3, you do the math.  I decided to give linux another try.  Personnally I grew fond of all the talk with Gentoo2006, but I couldn't get it to work with my Sata harddrives worth anything, tried several times and looked for help.  Then, I tried someting with a little more automation for the install, Suse9.3 everything seemed all fine until it tried to boot after Grub and all I got was a 3 inch green line at the top right of my screen to reward me, (yay!).  After trying many times to reconfigure the partitions and change the conf files I was about to give up.  "So, i'll give it one more shot," I said.  I did more research, took a little personality test for linux, and found that Debian was a high match did some research and found Ubuntu, I remebered seeing a few message boards talk about it so I decided to try **Ubuntu.** 

"Sweet just one cd to install, not a 4 dollar dual-layer dvd like Suse!"  I popped it in didn't look back just kept hitting enter, did all my account stuff and waited a few minutes.  Then the all great and mighty reboot....the-30s-wait..... loaded and worked fine the first time! Even had all the software I wanted on a fresh install.  I was very pleased.

After, almost lossing faith that no linux could be compatiable with my hardware I found Ubuntu (love at first sight [of the desktop])!

Thanks!

One note i'm trying to do some programming for these languages and was wonder if anyone knew of some good linux programs that work with Ubuntu I could use.

I need it for the following:
-Assembly Intel-Based  
-C
-C++

---

### Post by bruce89 on 2006-05-26
The command line with GCC, or for a graphical thing, Anjuta.

---

### Post by Lord Illidan on 2006-05-26
Just do ```
sudo apt-get install build-essentials
```.

This will give you the basics required for compiling programs.. Then get Anjuta or Kdevelop from the repos, and start rockin!

---

### Post by Harold P on 2006-05-26
It's **build-essential**, not build-essentials. So:

> apt-get install build-essential

Make sure you run it as root. ;)

---

