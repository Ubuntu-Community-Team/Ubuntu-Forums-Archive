---
title: "How to reduce the memory usage of Lubuntu?"
date: 2011-04-26
forum: General Help
---

### Post by Mark Meting on 2011-04-26
[SIZE=3][FONT=Calibri]Dear all,[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I installed the latest Lubuntu at the weekend on an 6-year-old-Laptop and there is one problem left:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Problem:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Lubuntu uses about 412mb of Memory (432mb total) even if just the taskmanager is open. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Question:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]How do I get more free Memory? [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Possible Solutions:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I tried to use tune2fs to add writeback, but I failed (I did not find the correct folder, I guess). How can I do this?[/SIZE][/FONT]
[SIZE=3][FONT=Calibri] Are there other opportunities to get more free Memory?[/FONT][/SIZE]
[FONT=Calibri][SIZE=3]Purpose:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I almost exclusively use the Laptop for watching mlb.tv (Baseball-Stream) in the internet. The Hardware can handle the data, because I had no problems watching the stream via the Windows XP-System which was installed on the same laptop.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Can you please help me?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Thanks in advance,[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Mark[/SIZE][/FONT]

---

### Post by AndyBoy_LV on 2011-04-26
Why not choose more lightweight distro? Like Puppy Linux, for example. It is extremely fast and lightweight, it can load itself into RAM completely.

---

### Post by Mark Meting on 2011-04-26
Thanks for your answer!
 
I am (and more important: my wife) used to Ubuntu, so I wanted to use an Ubuntu-like OS. 
 
Everything I need is 100mb of free memory more. Then everything will run smoothly. 
 
I still think, that this can be solved by the right tune2fs command. 
 
If there is no possibility to see the stream in a good way under lubuntu, I will switch to another distribution.

---

### Post by mörgæs on 2011-04-26
This sounds reeeally strange. Please post the output of

```
free -m
```

---

### Post by mcduck on 2011-04-26
> **mörgæs said:**
> This sounds reeeally strange. Please post the output of

```
free -m
```

+1 to this. Even my full Gnome setup doesn't use that much RAM, and considering my Ubuntu/Openbox system runs around 40MB of used memory it would be rather strange if a Lubuntu system really used *that* much more.

(and no, tune2fs has absolutely noting to do with your memory usage. It's a tool for adjusting the properties of Ext filesystems.)

---

### Post by mörgæs on 2011-04-26
A good one to read:

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by Mark Meting on 2011-04-26
Thanks for all your help!

My Numbers are:

Mem total: 432
Mem used: 241
Mem free: 190
Mem shared: 0
Mem buffers: 40
Mem cached: 116

+/- buffers/cached:
used: 85
free: 347
Swap: 
total: 496
used: 0
Swap: 496



So I guess, my memory is not the problem...

Okay, than the next question: How can I improve the system to run the internet stream faster?

---

### Post by AndyBoy_LV on 2011-04-26
I would say that this is up to your Internet Speed, not Linux

---

### Post by AllGamer on 2011-04-26
not quite, i think the problem is the browser

old Firefox or browsers are kind of slow at rendering items, specially on an older machine.

so i doubt the issue is bandwidth speed per say, but rather the browser rendering speed.

i wonder if it'll be possible to compile Firefox4 for an older linux

---

### Post by lithopsian on 2011-04-26
Memory looks fine.  You said it was using 400MB at the basic desktop but I don't see it.  Looks like around 100MB used plus around 100MB of disk cache, which is about what I'd expect.  The disk cache will steadily increase until it appears that you have no RAM free (or even swap being used!) but you always need to subtract that out to see your actual free memory.

Firefox 4 for an older distro?  Firefox 4.0 should run on any version of Ubuntu going back a long way.  There are library dependencies but they are very basic versions (apparently some CentOS versions need library updates, but CentOS is renowned for using libraries from about ten years ago).  Download it and try, you don't have to sit and wait for someone to build a deb for you.  4.0 is significantly faster than 3.6 in almost every way.

My Crunchbang distro (based on Jaunty but now upgraded to Karmic) boots up to a graphical desktop (Openbox plus Tint2 panel) using less than 50MB of memory.  Maverick uses more, but the main difference is the desktop.  Replace Metacity with something lightweight and disable services you don't need, you should be well below 100MB at the desktop.  Also check your graphics drivers aren't grabbing main memory, which is common for onboard graphics, and often they will grab far more than they need. You can get an idea of RAM hogs by looking in dmesg and /var/log/Xorg.0.log to see how much the kernel is grabbing and then running:
```
ps aux --sort rss
```

---

### Post by snowpine on 2011-04-26
The problem is the Adobe Flash Player; it simply runs slower in Linux than in Windows. This is proprietary "closed source" software so there is nothing really that you or the makers of Lubuntu can do to improve it. 

My solution is to use mlbviewer instead of the mlb.com website. This plays the game through mplayer instead of the browser and performance is a lot better.

[http://www.linuxquestions.org/questions/fedora-35/mlb-tv-in-linux-432479/](http://www.linuxquestions.org/questions/fedora-35/mlb-tv-in-linux-432479/)

(It's a huge thread, so skip to the last few pages if you want the 2011 instructions)

---

### Post by Mark Meting on 2011-04-27
Thanks for all the help. Unfortunately I am on a business trip and will find time to check everything just at the weekend. I will give feedback then.
 
Mark

---

### Post by dino99 on 2011-04-27
by defauly linux (ubuntu) use as much ram he can then use swap partition if needed, so dont worry (can be modified tweaking swappiness setting).

But its easy to:
- not use heavy apps like FF/Flash/Java
- deselect apps/services from: system-pref-starting_apps
- select & install lightest app(s) alternative from synaptic

---

### Post by Mark Meting on 2011-05-05
Dear all,

thanks for your help. The problem is solved after installing mlbviewer. Everything runs perfect now.

---

### Post by snowpine on 2011-05-05
mlbviewer rocks!

GO SOX!!!

---

