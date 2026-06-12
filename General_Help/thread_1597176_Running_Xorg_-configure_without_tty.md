---
title: "Running Xorg -configure without tty?"
date: 2010-10-15
forum: General Help
---

### Post by PoopLoops on 2010-10-15
Okay, long story short, computer crashed, wanted to see if I could salvage anything from the hard drive, but it turned out the current version of Ubuntu on it was somehow better than the version on my backup computer. No idea how, I did a clean install of 10.04 on the backup and it wasn't doing what I wanted, graphics-wise (I have an ATI card :( )

Anyway, managed to get sound working and everything else is fine, despite a different chipset and processor. Only problem is getting graphics to be *perfect*. I found some advice that I have been able to follow so far, except it wants me to edit my xorg.conf file with custom settings. Well, this being the newest xorg, it doesn't have a standard xorg.conf file. No worries, I found something that will generate one for me: "sudo Xorg -configure". Except that I can't run it while gdm is running. ...and I can't do anything once I do stop it. 

Okay, so I'm used to be dumped to a tty once I stop gdm or just hit ctrl+alt+F[1-6]. However, instead I am just greeted with a totally dark screen. Monitor claims there is no input and goes to sleep. I can hit ctrl+alt+F7 to get back to my desktop, so the computer isn't frozen.

I tried a bunch of different things to get tty working, but no dice. Recovery mode did work, though, but I had to have root access. So when I created the new xorg.conf file, it was for root and not my standard user. It was also kinda crappy, so I'm hesitant to just copy-paste it over.

So I guess my question is... any advice on how to proceed? :confused:

---

