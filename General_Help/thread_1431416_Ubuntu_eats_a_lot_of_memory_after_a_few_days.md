---
title: "Ubuntu eats a lot of memory after a few days"
date: 2010-03-16
forum: General Help
---

### Post by Hund on 2010-03-16
Ubuntu, well the apps to be exact, eats a lot of memory after a few days and it's really annoying.

Today when I started my second virtual machine all of my 6GB RAM wasnt enough and I barley managed to kill the machines to free some memory.

When I run my normal standard apps I use about 3GB RAM. Take the light Twitter client as an example, it should be a light client but it's eat almoust 400MB RAM.

Why do the apps use so much memory?

---

### Post by DawieS on 2010-03-16
It definitely looks as if you have a problem there...
Just for comparison look at my memory usage at the moment. (Total about 320 MB)

What version are you using?

I reboot at least once a day. If memory of old/closed processes is not reclaimed, I would not really  notice it. How often do you reboot?

---

### Post by soltanis on 2010-03-16
My memory usage is around 260 MB (minus cache which brings it to 592 MB out of my total 1015 MB), but I turn this computer on/off often. Still, for comparison, one of the servers I administer has an uptime of 15 days and is using only 188 MB + 764 MB cached, out of 2 GB total.

Seriously, something's wrong if you're using that much memory after only a few days of operation. What are you running, normally?

---

### Post by falconindy on 2010-03-16
Use a proper system monitor like htop. Gnome System Monitor eats a lot of memory on its own and lies about actual usage. You're seeing inflated numbers because it's including cached memory which is not actually in use.

---

### Post by prodigy_ on 2010-03-16
> **falconindy said:**
> Use a proper system monitor like htop.
I second that. Try ```
ps aux -o rss,cmd
```
Output is in KiB. If you won't see the same large values, there's nothing to worry about.

---

### Post by KinKiac on 2010-03-16
Whoa, 3g normally?  What the heck do you have running in the background?  I only have 3g ram.  Ive never seen myself go over 30% usage.  Sitting idle I use a few hundred meg, no more, and even if i have my IM and firefox going it still doesnt top 1g memory usage.  I dont even think my swap partition has ever been used, lol.  i barely ever reboot and ive had 9.10 installed since it was released.  There is definitely something wrong with your system, or the system monitor is lying as others have stated.

---

### Post by ManyuX95 on 2010-03-16
You know, my computer only uses between 400 mb and 600 mb out of a gigabyte. It's weird what happens to your pc, do you use 64 bit version? have it happened before with another distro? Im sorry if I did not helped you :D

---

### Post by Hund on 2010-03-16
> **DawieS said:**
> It definitely looks as if you have a problem there...
Just for comparison look at my memory usage at the moment. (Total about 320 MB)

What version are you using?

I reboot at least once a day. If memory of old/closed processes is not reclaimed, I would not really  notice it. How often do you reboot?

I'm using Lucid, it was the same thing with Karmic. 64-bit ofc. :)

6,5 days since the last reboot. Usally reboot once every 2-3 weeks maybe.

> **soltanis said:**
> My memory usage is around 260 MB (minus cache which brings it to 592 MB out of my total 1015 MB), but I turn this computer on/off often. Still, for comparison, one of the servers I administer has an uptime of 15 days and is using only 188 MB + 764 MB cached, out of 2 GB total.

Seriously, something's wrong if you're using that much memory after only a few days of operation. What are you running, normally?


I'm using 3887MB atm, 5981MB including the cache. I have 6GB total.

I'm running the usual stuff right now:

GNOME Terminal
Conky
Compiz
Deluge
Firefox
Gmail Notify
RSS Owl (Liferea doesnt work atm)
LinuxDC++
Pidgin
Pino
Screenlets
qBittorrent
Rhythmbox
Xchat

> **falconindy said:**
> Use a proper system monitor like htop. Gnome System Monitor eats a lot of memory on its own and lies about actual usage. You're seeing inflated numbers because it's including cached memory which is not actually in use.

I use htop to, heres a screenshot with it: [http://pici.se/pictures/cUgjyRhtZ.png](http://pici.se/pictures/cUgjyRhtZ.png)

> **prodigy_ said:**
> I second that. Try ```
ps aux -o rss,cmd
```
Output is in KiB. If you won't see the same large values, there's nothing to worry about.

That didnt work?

> johan@Tiji:~$ ps aux -o rss,cmd
ERROR: Conflicting format options.
[...]

> **ManyuX95 said:**
> You know, my computer only uses between 400 mb and 600 mb out of a gigabyte. It's weird what happens to your pc, do you use 64 bit version? have it happened before with another distro? Im sorry if I did not helped you :D

Yepp, I'm using the 64-bit version ofc. :) Never tried another distro, I'm to lazy for that.

---

### Post by prodigy_ on 2010-03-16
Ahh, really sorry. Indeed, **u** option is wrong in this case. :-) Omit it.```
ps ax -o rss,cmd
```

It's just hard to believe that your system would work at all if memory management were indeed broken and every app were allowed to leak memory indefinitely. It's even harder to believe that such situation could persist despite a major upgrade.

---

### Post by d3v1150m471c on 2010-03-16
```

free -m

```

---

### Post by Hund on 2010-03-16
I do think it's a lot of memory usage:

> johan@Tiji:~$ ps ax -o rss,cmd
[...]
315112 /usr/bin/python /usr/bin/deluged
524708 /usr/lib/firefox-3.6/firefox-bin [http://mail.google.com](http://mail.google.com)
297516 /usr/bin/X :0 -br -verbose -auth /var/run/gdm[...]
208468 python ./notifier.py
105096 pidgin
80908 gnome-panel
174124 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOM
405016 /usr/bin/java -DdisableUpdate=true -jar /usr/share/rssowl/plugins/org.ecl
426960 pino
203756 nautilus
228432 rhythmbox

---

### Post by Hund on 2010-03-16
> **d3v1150m471c said:**
> ```

free -m

```

```
johan@Tiji:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          5981       5930         51          0         22       1964
-/+ buffers/cache:       3944       2037
Swap:            0          0          0
```

:)

---

### Post by prodigy_ on 2010-03-16
> **Hund said:**
> I do think it's a lot of memory usage:
Yeah, this is abnormal...

What does ```
vmstat -s -SM
``` say? Do you use any proprietary drivers?

---

### Post by Hund on 2010-03-17
I'm using the proprietary driver for my NVIDIA card.

```
johan@Tiji:~$ vmstat -s -SM
         5981 M total memory
         5933 M used memory
         3743 M active memory
         1894 M inactive memory
           48 M free memory
           14 M buffer memory
         1937 M swap cache
            0 M total swap
            0 M used swap
            0 M free swap
     22603204 non-nice user cpu ticks
       551546 nice user cpu ticks
      6756338 system cpu ticks
     77445804 idle cpu ticks
      2524177 IO-wait cpu ticks
       575538 IRQ cpu ticks
       961460 softirq cpu ticks
            0 stolen cpu ticks
    394445997 pages paged in
    155417966 pages paged out
            0 pages swapped in
            0 pages swapped out
   2213736344 interrupts
   2690456498 CPU context switches
   1268242701 boot time
       800975 forks
```

---

### Post by prodigy_ on 2010-03-17
> **Hund said:**
> I'm using the proprietary driver for my NVIDIA card.
I don't want to jump to conclusions, but the apps that seem to consume your memory - aren't they all GUI apps?

Other than that, I see nothing unusual. Try to disable nVidia driver for a few days (if possible) and see if anything will change. If you use Compiz, it can be the culprit too.

---

### Post by soltanis on 2010-03-17
More than the video driver itself, I would suspect compiz. That thing is a crash waiting to happen, even though it's come a long way.

That is, if you're running it.

---

### Post by Hund on 2010-03-17
> **prodigy_ said:**
> I don't want to jump to conclusions, but the apps that seem to consume your memory - aren't they all GUI apps?

Other than that, I see nothing unusual. Try to disable nVidia driver for a few days (if possible) and see if anything will change. If you use Compiz, it can be the culprit too.

Yepp, it's all GUI. :) I tested the open source driver for my card a few days ago, but I wasnt even able to boot with em.

> **soltanis said:**
> More than the video driver itself, I would suspect compiz. That thing is a crash waiting to happen, even though it's come a long way.

That is, if you're running it.

I've been using Compiz a few years (Beryl back then) and they have been working fine all the time. But I'll disable Compiz and see whats happends.

---

