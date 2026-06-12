---
title: "Zombie got into my computer"
date: 2011-08-28
forum: General Help
---

### Post by Jerriy on 2011-08-28
I dunno what happened lately (what kinda update or tweak happened yesterday or today but something did happen and as a result whenever I'm in firefox it suddenly is extremely slow.

I wanted to find out what was running and I opened "system monitor" and noticed that there was a new until now non-existent file in my sysmonitor list of running files: this was a new, second "firefox bin" and it was in a permanent "zombie" status rather than "running" or "sleeping" like the preexisting firefox bin.

I dunno what the heck it is, where it came form, and what it's doing and where it's going but I want it out of my system. 

It's guzzling my memory and it's slowing down my browser dramatically (by more than tenfold seconds during certain routine simple commands like right-click options) 

Needless to say this is unacceptable. 

My request is first and foremost (1) What's the solution? and (2) what devil caused it to sneak into my computer?

---

### Post by jerrrys on 2011-08-28
you can't  do a killall firefox?

---

### Post by Jerriy on 2011-08-28
No after I kill it and restart firefox the zombie "firefox bin" rears it's ugly head again. 

Like a horror movie villan it reappears again and again and I'm so far unable to kill it and open firefox at the same time

---

### Post by jerrrys on 2011-08-28
make a copy of >.mozilla and purge and reinstall firefox.  ff5 is actually fast...

---

### Post by Jerriy on 2011-08-28
Am I hacked?????

---

### Post by Jerriy on 2011-08-28
> **jerrrys said:**
> make a copy of >.mozilla and purge and reinstall firefox. Then I'm supposed to replace the new .mozilla with my saved one?

> ff5 is actually fast...Indeed, I know. It WAS fast in my system as well.

---

### Post by Jerriy on 2011-08-28
This looks creepy:[QUOTE=Wikipedia][Zombie computer]("https://secure.wikimedia.org/wikipedia/en/wiki/Zombie_computer"),  sometimes referred to simply as a zombie, a computer accessed by a  hacker without the owner's knowledge and used for purposes such as  sending spam[/QUOTE]

---

### Post by jerrrys on 2011-08-28
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=zombie&sa=Search&cof=FORID:9#851](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=zombie&sa=Search&cof=FORID:9#851)

---

### Post by Blackra1n on 2011-09-04
> **Jerriy said:**
> I dunno what happened lately (what kinda update or tweak happened yesterday or today but something did happen and as a result whenever I'm in firefox it suddenly is extremely slow.

I wanted to find out what was running and I opened "system monitor" and noticed that there was a new until now non-existent file in my sysmonitor list of running files: this was a new, second "firefox bin" and it was in a permanent "zombie" status rather than "running" or "sleeping" like the preexisting firefox bin.

I dunno what the heck it is, where it came form, and what it's doing and where it's going but I want it out of my system. 

It's guzzling my memory and it's slowing down my browser dramatically (by more than tenfold seconds during certain routine simple commands like right-click options) 

Needless to say this is unacceptable. 

My request is first and foremost (1) What's the solution? and (2) what devil caused it to sneak into my computer?

I have this same problem with three different computers (two desktops and one laptop). I have tested Ubuntu 11.04, Xubuntu 11.04 and Ubuntu 11.10 beta 1 and they all have this strange firefox zombie problem! Can someone help?

---

### Post by Blackra1n on 2011-09-04
Anybody else have this problem? This bug is very easy to reproduce: Just start firefox and run top to check for zombie process.

---

### Post by spiky001 on 2011-09-04
Can you post a screen dump of top

---

### Post by texaswriter on 2011-09-04
I have never seen that even once. 

Usually when I run firefox, I get one process, "firefox-bin". 

Chromium, on the other hand, spawns separate "sand-boxes" for tabs and plugins (i believe), so you will often see many chromium-browser processes if running Chrome or Chromium.

---

### Post by hakermania on 2011-09-04
Not reproducible here as well, you can post a bug about firefox you know...

---

### Post by JKyleOKC on 2011-09-04
Don't confuse the "zombie process" reported by top with the "zombie system" described in wikipedia. Linux uses the term "zombie process" to describe a process whose status information has become inaccessible for any reason; no intrusion from outside is involved. Once a process becomes a zombie, the "kill" command won't work on it any more -- hence the name.

The best way I've ever found to reliably kill a zombie process is to simply re-boot the system. That will kill all processes regardless of their status. If that's not an option, you can usually kill one by killing its parent process (identified by the PPID column in the "top" report) but that can sometimes lead to file corruption, if the parent process has other processes running also that happen to be writing to files. The re-boot is much safer!

As for what causes them, it's usually due to some sort of unhandled error within the program. The place that I've gotten zombies created most often was my favorite text editor, and I never did manage to figure out what was causing them -- but eventually they did quit happening.

---

### Post by Primefalcon on 2011-09-04
a kill -9 sometimes works on zombies but... not always

---

### Post by Blackra1n on 2011-09-05
> **JKyleOKC said:**
> Don't confuse the "zombie process" reported by top with the "zombie system" described in wikipedia.

I have made no such claim. (I know what zombie process is) :)

---

### Post by Blackra1n on 2011-09-05
I think that this bug has something to do with recent firefox updates.

---

### Post by Duncan Williams on 2011-09-05
On my system zeitgeist-datah is a zombie.
this shows as a bug in launchpad.
[https://bugs.launchpad.net/ubuntu/+source/zeitgeist/+bug/753984](https://bugs.launchpad.net/ubuntu/+source/zeitgeist/+bug/753984)

Probably nothing to do with this FF in zombie state though.

I am interested to see where this goes...

---

### Post by JKyleOKC on 2011-09-05
> **Blackra1n said:**
> I have made no such claim. (I know what zombie process is) :)I had no intention of accusing you, or anyone else, of anything. See post #7 of this thread, by the original poster; I simply wanted to point out that the implication of that post had nothing to do with the original problem of a zombie process.

It appears that this **might** be a bug in Firefox introduced in one of its recent updates. I don't see such a problem here, but am staying with the 3.6 version (currently at 3.6.21) for now since I've seen many reports of problems with the newer ones...

---

### Post by Bluesan on 2011-09-05
Many articles like this, are available, if you take the time to look for them...

**Undead and Open Source: Zombie Processes in Linux Explained**

> You might have seen zombie processes listed along with your Linux  computer's other processes. But what are they and why cant they be  killed like normal processes?[http://www.brighthub.com/computing/linux/articles/79186.aspx](http://www.brighthub.com/computing/linux/articles/79186.aspx)

Edit:

And, for anyone confusing Windows with Linux, it would probably be worthwhile to read this too...

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by philinux on 2011-09-05
Zombie Explained.

[http://en.wikipedia.org/wiki/Zombie_process](http://en.wikipedia.org/wiki/Zombie_process)

And

[http://askubuntu.com/questions/48624/what-are-zombie-processes](http://askubuntu.com/questions/48624/what-are-zombie-processes)

---

