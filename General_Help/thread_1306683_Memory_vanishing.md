---
title: "Memory vanishing"
date: 2009-10-30
forum: General Help
---

### Post by mollyj on 2009-10-30
can anyone help. I have been using ubuntu hardy for about a year or so and recently it has started locking up. I've looked at the system monitor and the memory usage is steadily rising even with 'nothing' running ."Once the ram is full the swap file starts to rise. I've looked at the forum history and have seen that one correspondent solved it by configuring firefox. However 1) I've been using firefox over the whole period and haven't noticed this before 2)When I look at the processes nothing appears to be using more than about 2%.
I did have a problem the other day when I accidentally clicked on an advert on the web and got the scam message about having 534 viruses. I didn't follow up any of the links I just closed down Firefox.  Then I probably did some thing stupid I downloaded the AVG virus scanner to check if anything had got infected (as I use my ubuntu machine for work; editing word stuff etc. and I can't afford to import viruses to the office).
I think that the problem with the memory started at about the same time. Hence I suspect the AVG.
I am not at all confident with Linux preferring to be a user rather than a GURU
How do I find out what's causing the loss and how can I stop it? I can live without the AVG (and get around the virus problem by scanning on the windows machine) but it seems to be there all the time in the process list. 
Any help would be appreciated.

---

### Post by earthpigg on 2009-10-30
hi,

install htop

```
sudo apt-get install htop
```

then, run it in a terminal and sort by MEM%

```
htop
```

---

### Post by doas777 on 2009-10-30
please note, you may have to run htop with sudo. some processes do not show by default unless you run with admin. gufw's python processes for instance.

do you think your ram may be cached rather than in use by a program? I have seen caching run amok before.
[http://ubuntuforums.org/showthread.php?t=589975](http://ubuntuforums.org/showthread.php?t=589975)

---

### Post by mollyj on 2009-10-31
Thanks for the support. 
I think that I've solved it or at least found the cause. Using a combination of the system monitor and htop I found that AVGscan was running. Since I suspected this I killed it. It re-appeared a few seconds later. I killed it again. and again and repeated the actions until it didn't seem to appear again. The memory and cpu usage dropped dramatically. Then another avg appeared; not a scan this time but what seemed like a schedule generator . I killed this as well. and this time the memory and cpu usage dropped to a reasonable level and stayed there (fingers crossed). I haven't investigated whether the thing re-appears when you reboot so I won't call this thread closed until I am sure that the problem has gone away.
BTW. I've noticed a similar effect on windows computers at work using a 'name' antivirus software. The system slows to a crawl and when you look at the equivalent of the system monitor app it appears that the AV software is hogging everything.

---

### Post by mollyj on 2009-10-31
the saga continues.
I re-booted and there were no fewer than 14 incarnations of avg each using 80meg of memory and growing. After some searching through the threads I tried to remove AVG using dpkg in a terminal window. It failed with a failed to find '/..../..../..../avg.pid' and avg was still there when I did a package query. I tried again using 'aptitude remove'. This time the command appeared to complete satisfactorily. I then used 'purge' and this also appeared to work. I re-booted and my memory usage was back down to about 120meg and the cpu down to less than 25%. 
This looks like it has solved the problem but I won't hold my breath..............

---

