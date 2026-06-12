---
title: "RAM issue in Lucid - performance being impacted"
date: 2010-06-24
forum: General Help
---

### Post by MattP220 on 2010-06-24
I've searched around and found that complaints of high RAM usage are common in Lucid, and the consensus seems to be that this is normal due to caching. Cool.

Here's my issue. I've got a new desktop that was freshly built a few weeks ago (dual-core Athlon 64-bit, 2gb RAM). I dropped Lucid on it straight out of the box. I also have run it on a laptop with nearly identical specs, and noticed the same issue I'm about to describe. 

I'd noticed the RAM-usage issue, in that at boot and without browsers running, it sits right around 50% memory usage in both desktop and laptop. Again, no problem there. What kills me is when I run Firefox and Chrome at the same time (which I often due for development reasons, and because I have various accounts set up in each). 

When that happens, RAM usage will push 85-90% or higher. If this were just caching I wouldn't care, but this actually causes the whole system to slow down. Tabbing between pages slows down, sometimes the whole desktop will freeze for a second or two, it can take up to 10 seconds to get the screen back from the screensaver, applications & menus are slow to respond, etc etc.

Killing one of the browsers will knock RAM usage back down to 70% or so and the sluggishness stops. 

This is pretty irritating, given that I could have an identical number of windows open (two browsers w/ several tabs, big GIMP image, multiple small apps in parallel) in previous versions with no problems. I've been using Ubuntu since 7.10 and never have seen anything like this. 

Any ideas what's going on here, besides Chrome and FF being memory hogs?

---

### Post by prshah on 2010-06-24
> **MattP220 said:**
> RAM usage will push 85-90% or higher... this actually causes the whole system to slow down.

I suggest you check the "swappiness" settings; I suspect it will be set a lot lower on your laptop than your desktop; from a terminal (Applications-Accessories-Terminal) check the swappiness settings on each machine:```
cat /proc/sys/vm/swappiness
``` 

Lowering "swappiness" will prevent swapping from starting early; for a 2GB desktop, I suggest you can use a swappiness of 10~20 (Which approximately means that memory swapping will start only when less than 10-20% of free memory remains).

To temporarily set and check a new swapiness value, do ```
sudo sysctl vm.swappiness=20
```

To permanently change the value, edit /etc/sysctl.conf, and change/add the "vm.swappiness" value, eg```
vm.swappiness=20
``` Reboot, or sysctl refresh needed for changes to take effect.

Please post back with your results.

---

### Post by MattP220 on 2010-06-24
I checked and swappiness was originally set to 60. I don't have access to the laptop at the moment (it's got a broken power switch) but when I get it back I'll give it a look.

I set vm.swappiness to 20 on the desktop as you suggested and *fingers crossed* it appears to be working - I'm getting ~70% usage instead of 90%. However that's immediately after restarting both browsers, so that may change.

Cheers for the input.

---

### Post by dcstar on 2010-06-24
> **MattP220 said:**
> 
..........
I'd noticed the RAM-usage issue, in that at boot and without browsers running, it sits right around 50% memory usage in both desktop and laptop. Again, no problem there. What kills me is when I run Firefox and Chrome at the same time (which I often due for development reasons, and because I have various accounts set up in each). 
........... 

Any ideas what's going on here, besides Chrome and FF being memory hogs?

Post the output of both PCs of this command when the problem happens:

```
free -m
```

---

### Post by prshah on 2010-06-24
> **MattP220 said:**
> I'm getting ~70% usage instead of 90%. 

Stuff that is already in the swap before change in swappiness will continue to get swapped in/out. For a real result, please check with a fresh boot (at your convenience) or by making it permanent (which will also require a fresh boot, so again at your convenience).

If you are uptime-zealot and don't want to (re)start  your computer, try this: (At your own risk):

a) Close down all running programs;
b) After a few moments, check to see if swap usage has dropped; 
c) if swap usage is less than your currently free memory (free -m) then give the comamnd```
sudo swapoff -a && sleep 5 && sudo swapon -a
``` Which essentially turns off your swap, waits a while and turns it back on again. When swap is turned off, theoretically swap stuff will be dumped to the main memory, and when turned on again, the low swappiness will prevent excessive or unnecessary swap usage.

Note this is an extreme action, and instead of this I would simply recommend you make the change in /etc/sysctl.conf and reboot. You can always change it back when you will.

Good luck!

---

### Post by warfacegod on 2010-06-24
> I'd noticed the RAM-usage issue, in that at boot and without browsers running, it sits right around 50% memory usage in both desktop and laptop. Again, no problem there.

Just like to point out that on a 2 GB RAM system, using 1 GB right after boot *is* a problem. I've got 2 GB in my laptop and when I boot into Lucid (rarely, grant you) it's never higher than 350 MB or so. I suggest using your System Monitor or htop to find out what is using all that RAM and either fix it or remove it if possible.

If you can find the culprit in this and deal with it, you should have no problem running F.F. and Chrome at the same time with allot of other apps as well.

---

### Post by MattP220 on 2010-06-24
@warface, that was my thought on the matter, but reading around apparently Lucid does have some crazy cache usage, so I was willing to write it off. 

@dcstar & prshah - I did a reboot just a bit ago (swappiness set to 20 permanently), and opened up a bunch of windows jsut to test the thing. 

The system monitor is showing me ~94% RAM usage. I have open FF w/ ~8 tabs, Chrome w/ ~4 tabs, Gwibber, sys monitor, and two terminal windows. Also a few background processes like empathy, dropbox, and vidalia. 

```
free -m
             total       used       free     shared    buffers     cached
Mem:          1754       1733         21          0          6         82
-/+ buffers/cache:       1644        110
Swap:         5720         64       5656

```

So, uh, yeah. Interestingly enough, I don't seem to be getting the sluggishness even with that high RAM usage; right now it seems to be humming along just fine as I test menus etc. 

But if warface is right and something is gumming up the works, I'd like to get it sorted.

---

### Post by warfacegod on 2010-06-24
I decided to reboot into my Lucid install to check my RAM use and to give you an idea of what your RAM use should be more like. The first shot is immediately after bootup/desktop ready. The second shot is after opening lots of stuff (obviously).

Please note than these shots do not account for RAM as Cache. For the first shot Cache was negligible. After the second shot RAM as Cache was 252 MB, still leaving about 1.35 GB RAM free.

P.S. Please ignore the shabbiness of my desktop. I rarely use Lucid and I have done little more than make the panels transparent and added my usual sinister background.

---

### Post by MattP220 on 2010-06-24
Wow. Yeah, that's a huge difference.

Contrast that to mine.

I really have no idea what's eating up the space. Sysmonitor doesn't show anything strange, top doesn't show any one process eating up an unusual amount of RAM...I did find something about a but in ureadahead that may be causing crazy RAM usage, but I haven't really followed up on it.

---

### Post by warfacegod on 2010-06-24
If my memory serves ureadahead logs or something were supposed to eat up ridiculous amounts of HDD space. I don't think I've heard of it playing games with RAM. Could be wrong, it's happened before.

Have you tried htop? It's sort of like a cross between top and System Monitor. It's got columns that you can set to display in descending order. Might make it easier to track done the culprit.

---

### Post by MattP220 on 2010-06-24
here's the htop output. What stands out to me is that there's a ton of PIDs going for FF, which don't show up in the sysmonitor. Chrome already shows up as multiple PIDs in sysmon. 

That explains why it maxes out when I have both open, but it still doesn't cover why it's using 50% on startup. I'll do more investigating.

---

### Post by MooPi on 2010-06-24
I would start with your startup programs and eliminate any unneeded apps. The only time my system has crested the 2 gig mark(out of 4 gig) is during a virtualbox running and multiple other apps. Your memory usage is literally off the charts.

---

### Post by warfacegod on 2010-06-24
> **MattP220 said:**
> here's the htop output. What stands out to me is that there's a ton of PIDs going for FF, which don't show up in the sysmonitor. Chrome already shows up as multiple PIDs in sysmon. 

That explains why it maxes out when I have both open, but it still doesn't cover why it's using 50% on startup. I'll do more investigating.

My Firefox has 12 PID's with one tab open. Each one is 2.9 MB.

moopi's idea about Startup Apps is a good place to start reining this in. But to be perfectly blunt, I don't see it taking more than 5% at most off your RAM after bootup.

---

### Post by MattP220 on 2010-06-24
Okay this is strange, and I have no idea if it's normal or not, but as I scroll through htop's output, I notice that there are several programs with mulitple PIDs running. 

Dropbox has about 15, Gwibber is hogging several (both the program and the Python backend), console-kit-daemon looks to have around 50-60, mysql has 10-15 (I'm running a LAMP server, for full disclosure), and /usr/bin/erlang has about 5-6 open that appear related to couchdb.

Besides that, a lot of smaller nitpick processes appear to be doubled or tripled. Is this just some Ubuntu artifact, or are each of these PIDs each eating up a chunk of memory?

---

### Post by MattP220 on 2010-06-24
> **warfacegod said:**
> moopi's idea about Startup Apps is a good place to start reining this in. But to be perfectly blunt, I don't see it taking more than 5% at most off your RAM after bootup.

That's just the thing, I don't really have anything besides the basic installation that kicks in on startup. Dropbox does, Conduit does, the Apache/mysql setup does, and that's about it. I haven't fiddled with any of the startup programs besides that.

---

### Post by warfacegod on 2010-06-24
The console-kit deamon is normal. I just counted mine and I've got 65.

---

### Post by psusi on 2010-06-24
There is a bug in ureadahead where it ties up a good chunk of memory ( up to 128 mb per cpu ) when it does a profile run, which it will do after you update/install packages.  Rebooting again should take care of it.

---

### Post by MattP220 on 2010-06-24
> **psusi said:**
> There is a bug in ureadahead where it ties up a good chunk of memory ( up to 128 mb per cpu ) when it does a profile run, which it will do after you update/install packages.  Rebooting again should take care of it.

Okay I just tried a fresh reboot to see what this would do.

Memory right at startup was 23%, and that eased up to 29-30% just at the start. I opened FF and that jumped to ~43%. Chrome shot it up to 62%. 

It seems to be hovering right around that right now. I'll update if there's any changes.

---

### Post by prshah on 2010-06-24
> **MattP220 said:**
> 
Memory right at startup was 23%, and that eased up to 29-30% just at the start. I opened FF and that jumped to ~43%. Chrome shot it up to 62%. 

With a LAMP server stack running simultaneously, I'd call this memory usage OK. Don't think you need to make any changes. As long as the sluggishness has gone away...

---

