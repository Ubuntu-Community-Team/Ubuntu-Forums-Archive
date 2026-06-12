---
title: "Still got memory leak in Lucid?"
date: 2010-05-03
forum: General Help
---

### Post by gvernold on 2010-05-03
Guys, I installed Beta 2 of Lucid 32bit about two weeks ago. I did all of the updates which seemed to solve a lot of problems but I still seem to have a memory leak somewhere.... I think.

When I first switch on the machine and use the free command I am using around 490mb of ram. After 30 minutes this is around 1010mb. After a full day of using nothing but Bluefish and Gimp (with Gimp closed after use) I have used my full 2GB of ram and crawling towards 600mb on swap. Presumably this is not normal but I want to know what I can do to test the system i have and report back on here.

Please not that I haven't used any other apps except Gimp and Bluefish with a basic Apache web server running in the background. My machine is Intel based with integrated Intel graphics.

---

### Post by hangfire on 2010-05-03
> **gvernold said:**
> Please not that I haven't used any other apps except Gimp and Bluefish with a basic Apache web server running in the background. My machine is Intel based with integrated Intel graphics.

Well, you have the right candidate h/w for the leak.

Can you find out where the leak is, an application or the kernel?

---

### Post by Erik765 on 2010-05-03
I would keep my eye on system monitor and sort by memory usage. Check back on it every now and then and see which app(s) seem to be leaking.

That should give you a place to start at least.

---

### Post by gvernold on 2010-05-03
Thanks guys, I will try and update on this thread this time (sorry about a couple of the others I haven't kept up with). Starting system monitor now, will post back later today or tomorrow.

---

### Post by PC_load_letter on 2010-05-03
Personally, I'd use "htop" instead. If you don't have it already, just type ```
sudo apt-get install htop
``` in a terminal.

It's a CLI only app, and it doesn't consume as much memory (IIRC) as the System Monitor. You start it from the terminal by typing```
htop
``` then click on "MEM" to arrange processes by memory consumption.

---

### Post by gvernold on 2010-05-03
Actually I've noticed this afternoon that System Monitor is giving me different data to free as well. Not sure which one to trust so I'll try htop and see which has the closest results.

---

### Post by PC_load_letter on 2010-05-04
I'm not sure of the current situation but the reason I started using htop, or even top (both CLI apps) is that I read here on the forums that System Monitor has it's own memory leak problems, or at least that it consumes quite a bit of memory. Maybe this has been fixed, but I'd trust CLI tools for memory monitoring for now.

---

### Post by gvernold on 2010-05-11
A quick update... I have been testing memory usage for almost a week now. Something is definitely leaking but I can't be sure what, it's just so slow to build up but it is there.

Also, I get different memory usage statistics from System Monitor, Htop and Free. Not by small amounts either, the differences can be huge. I've read as many instructions as I can find to make sure I'm using all the above correctly but the statistics still come out different.

---

### Post by hurdevan on 2010-05-19
Brief summary: Ram climbs to to a nice 800 MB with cache of 300 or 400.) The leak only happens when the computer is being used. The problem is fixed when Compiz is turned off.   


Have have had this problem ever since switching to 10.04 and the leak has been driving me nuts. Searching Google I find that there are so many post saying that it's just Ubuntu using the access ram. No DUH
Ubuntu is not suppose to be using this much, EVER. Before my switch my system would typically use under 500MB(really around 300MB) and 0MB of cache. However, now over a progressive amount of time + usage my system will get up to 800 MB of ram and 400 in the cache.

However, this might be a compiz leak I think. Turning off Compiz fixes everything. My system will use around 300Mb of ram without even touching the cache.

But I think my system justs hates me. It only leaks when I am on it. I can leave it sitting their all night after a fresh restart with Google Chrome open and it will stay at a nice 300MB. But, when I start browsing the web then my ram starts climbing. I thought that it might have been a browser leek but the results are the same with both Firefox and Chrome. 

What really ticks me is that I can't see where the leak is coming from. The system monitor says that I am now using 530 MB of ram(1 Minuet ago it was 527... Slowly climbing) But when I do that math and count the ram consumptions of each process then I get a normal amount...around 300MB.  

The conclusion is that its probably a Compiz or Xorg leak. It might be one of the Compiz plugins. I don't know.

---

### Post by philinux on 2010-05-19
It's most likely this bug.

[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)

---

