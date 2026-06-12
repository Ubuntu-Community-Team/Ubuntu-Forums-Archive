---
title: "Ubuntu 10.10 not booting past checking battery state"
date: 2010-12-26
forum: General Help
---

### Post by blondyman1503 on 2010-12-26
Every time I try to boot into Ubuntu, it never goes any further than “Checking battery state...”
Once it gets there it pauses for about 2 minutes then goes to “^@” and doesn't go any further. I can still press CTRL+ALT+F(1-6) to get to a command line, but I'm kinda n00bish when it comes to the command line. 

Any ideas of what I can do?

---

### Post by Siramau on 2011-01-16
Same problem here :(. It seems to be semi-common,  but I haven't seen any solutions.

---

### Post by blondyman1503 on 2011-01-16
so I found a way around this.
I went into ctrl+alt+f1 and did ```
sudo apt-get install kdm 
```
Once it finished installing I restarted and a window popped up and said that Ubuntu was running in low graphics mode. I chose to run Ubuntu in low graphics mode. Then everything continued on as normal.

---

### Post by Siramau on 2011-01-16
Huh, interesting. Won't install for me, getting  ```
 Could not resolve 'us.archive.ubuntu.com
```Glad you figured it out though.

---

### Post by fishtron on 2011-01-30
Hey Siramau, make sure you're connected to the Internet via ethernet cable, wifi drivers won't be loaded at that point yet. Try to ping google.com and see if you get any traffic through. I had to do that on my laptop even though wifi works normally.

Anyway, I have the same stalling problem at boot as y'alls after installing nvidia-current... on a previous-working instance of Maverick. I'm installing kdm now to see if that helps. Tried purging & installing gdm to no avail.

---

### Post by Lyron on 2011-11-14
[FONT=Verdana][SIZE=2]I know this post is old but...

To anyone that have the issue stated above: How much free space do you have on your Hard drive? Too little space can cause Gnome power management to stop. Try to free some space using a live cd (let´s say 5 gb) and reboot your machine. Now it should start normally.[/SIZE][/FONT]

---

