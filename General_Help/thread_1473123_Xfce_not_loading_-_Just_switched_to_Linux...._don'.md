---
title: "Xfce not loading - Just switched to Linux.... don't want to go back"
date: 2010-05-04
forum: General Help
---

### Post by TechnoFou on 2010-05-04
Hi there,

   I juste recently tried Linux with Wubi and, I really loved it so I made it my primary OS. I made it like I wanted it with Compiz, Emerald, Chrome etc.... but now it doesn't want to load anymore and just before everything was right.

I just switched so I'm no expert.

When it loads it goes under command line mode. I login and when I write XFCE4-PANEL it gives me:

*"xfce4-panel: Cannot open display:"*

If I try DISPLAY:

*"display: unable to open X server '' @display.c/DisplayImageCommand/422."*

If I try to go under RecoveryMode I tried to clear the bad packages, still nothing. I also tried to go in under FAILSAFEX and it says:

[I]"Fatal server error:
 no screens found"[/I]

It is an integrated card (graphics ATi) and I am positive on the fact it still works fine (tested it)

I really like Linux but already the whole "Use a lot of command to do tasks" is quite rough, if these things happens a lot...... I think I'll go back to Windows.. because I master this OS like my pocket.

Thanks all !! really appreciate it !

Xubuntu 10.04 Lucid Lynx

---

### Post by cariboo on 2010-05-04
I would suggest you start in recovery mode, when you get to the menu select drop to root prompt with networking. Once at the prompt type:

```
apt-get -f install
```

once that is finished type at the same prompt:

```
sudo aptitude update && sudo aptitude -y safe-upgrade
```

The above two commands should fix any problems with broken packages, and make sure you are up to date.

Using a Linux variant is just like using Windows, it takes time to learn how to use it properly, after all none of us were born knowing how to use windows.

---

### Post by TechnoFou on 2010-05-05
No it didn't work :(

I tried it and it only added a new option on the boot from 21 to 22 kernel...... Still the same thing...

:( ??

---

### Post by TechnoFou on 2010-05-07
Anyone got an Idea.... There isn't a kind of System Restore in Linux ??

---

### Post by cariboo on 2010-05-07
I refuse to use ATI grahics cards, but depending on which driver you are using we should be able to get you up and running. When you start in recovery mode, just let it go until you get to the prompt, after you log in with your user name and password, at the prompt type:

```
sudo service gdm start
```

to see if that takes you to the desktop.

---

### Post by TechnoFou on 2010-05-08
OMG IT WORKED !!! thanks so much :D I used your technique and I checked a bit on the internet and I'm back to my desktop :D

Nice, I'll go switch all of my PCs now :) !!

Thank you VERY MUCH sir !

---

