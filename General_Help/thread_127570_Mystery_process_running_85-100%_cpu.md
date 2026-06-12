---
title: "Mystery process running 85-100% cpu"
date: 2006-02-09
forum: General Help
---

### Post by earth_walker on 2006-02-09
I have recently had a successful install of Ubuntu to my laptop (how-to in the works). 

When I woke it up this morning and logged in (no suspend2 yet, so it was just running all night), the cpu monitor applet showed a process running 85-100% of the cpu, and the harddrive was whirring busily.

This went on for about 20 minutes. Nothing else was running. Gnome system monitor showed nothing taking up more than 7% cpu, and that was xorg, followed by a small amount for gnome-system-monitor, and then a bunch of sleeping processes. Top gave similarly unhelpful results. I even logged out and in again, and once everything came up the system settled back to a steady 85% processor use with the harddrive whirring.

And just as I started to write this, it stopped and the cpu and harddrive have settled down again. Very mysterious. This has never happened that I've noticed on my two ubuntu desktops

After many months of enjoying the freedom, security and control (I should write shrub foreign policy...) in linux, this has been a rather disturbing windows-like experience. What could the mystery process be? Why could the tools I was using not find it even though the applet could see it?

How am I going to feel safe in a linux world I can't control???

---

### Post by lamego on 2006-02-09
If the cpu is really at high utilization the processes must show up on "top", if is not just a single process you should find a very high process count (small processes "eating" your cpu).
If you can't find this processes with top/ps  then your applet is broken :)

---

### Post by earth_walker on 2006-02-09
Although I didn't pull my calc out, I did do a quick mental addition of cpu loads and it wasn't more than 20%. There were only 2-4 processes that weren't sleeping. I wish I could reproduce it and post the results, but alas, I'll have to keep an eye on it.

Are there any scheduled tasks which the operating system does automatically, which take 15-20 minutes, write to disk alot, and would either start every morning or after sitting idle for 12 hours?

---

### Post by earth_walker on 2006-02-12
Well, it wasn't my imagination - it happened again this morning. I took it out of sleep, and for about 15 minutes the cpu was at 99%, the hd whirring away, but top and gnome-system-monitor show a total of three to four processes using 13% cpu. 

Anyone else notice this behaviour?

---

### Post by Ocxic on 2006-02-12
is it possible that your running some type of automated backup?

---

### Post by earth_walker on 2006-02-12
No, afaik nothing that I've installed would cause this type of behaviour. I did a little fiddling by closing down various applets to see if anything may help, and when I tried to turn off the gnome battery applet, X crashed and linux went through the shutdown process. So that is my latest suspect...

---

### Post by newuser111 on 2006-02-12
its not helpful since you dont name the actual process name

maybe gam_server, which is gamin, the file monitoring daemon, some have noted its huge memory leaks, but I strangely have never had a problem with it on many installs

---

### Post by Ziggy Stardust on 2006-02-12
Could it be updatedb? It runs once a day and goes through the filesystem to find changes made since it ran the last time. It basically creates a database of your files, so you can find them quickly using slocate.

---

### Post by earth_walker on 2006-02-14
Thanks for your suggestions. I have to wait until I see it doing it again before I can test any of these theories, and of course since top doesn't seem to show the activity I'm not sure how I can tell what's going on even if I knew the name of the process doing it! I'll keep posting as I get more info.

Since both times it happened right after I brought it out of sleep (when I close the laptop lid it locks the screen - I'm not sure whether any other 'sleep' functions are activated, as it will still play media), but hasn't happened any other time, I'm wondering if this is acpi- or suspend- related?

---

### Post by shawnzyoo on 2006-02-14
I just have noticed the same lately
but I found it to be that Gnome-Panel is eating up like 80%
so i kill it and gnome still works fine.....weird
anyone know whats going on?
thanks

---

