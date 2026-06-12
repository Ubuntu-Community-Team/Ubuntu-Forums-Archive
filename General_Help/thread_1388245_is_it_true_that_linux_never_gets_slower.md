---
title: "is it true that linux never gets slower?"
date: 2010-01-22
forum: General Help
---

### Post by sincerelyydavid on 2010-01-22
read that from here: [http://www.whylinuxisbetter.net/items/old_and_sluggish/index.php?lang=](http://www.whylinuxisbetter.net/items/old_and_sluggish/index.php?lang=)

and then here: [http://www.whylinuxisbetter.net/items/defragment/index.php?lang=](http://www.whylinuxisbetter.net/items/defragment/index.php?lang=) it says that "The more you use Windows, the slower  it is to access files ; the more you use Linux, the faster it is." is that true also?

---

### Post by Miljet on 2010-01-22
I wouldn't say that Linux get faster, but it is true that the disk never gets fragmentated. Another things that slows Windows over time is all the registry entries that get left behind whenever you remove some program.

---

### Post by Dennis N on 2010-01-22
In my experience, Windows XP became slower especially in the time taken to boot up and shutdown as went on, while Linux does not. 

I wound not claim that Linux gets faster, however.

---

### Post by d3v1150m471c on 2010-01-22
check out "preload". it's in your synaptic package manager. The only problem you might run into with linux getting slower is if you leave your computer running for weeks, maybe even longer, and your cache and ram usage fills up. Solved by restarting.

---

### Post by scouser73 on 2010-01-22
I've never experienced a slowdown in Ubuntu in the time that I've been using it.

---

### Post by warfacegod on 2010-01-23
There are days when my laptop is speedy and other days it's a bit mopey. Perhaps even vaguely sluggish but never slow. If you experience a slow down in Linux it generally means you got an app running that uses allot of horsepower, the is something very badly configured in your install, or you're have a hardware failure. Of the three, the first is, by far, the most common.

---

### Post by JiuJitsu500 on 2010-01-23
> **Miljet said:**
> I wouldn't say that Linux get faster, but it is true that the disk never gets fragmentated. Another things that slows Windows over time is all the registry entries that get left behind whenever you remove some program.

Don't jump to conclusions on that one, all file systems can and will eventually get fragmented. But, since Ext (journalling) file systems store things so far apart (in an organized manner) and so differently, you should never really worry about it except when using more than 80% or so of your disc space.

To avoid any and all trouble with Linux and fragmentation, simply store everything in an external hard drive and keep the HDD with linux on it less than 50% full.... then this is very true :)

As for getting faster, I think that's definately an overstatement, but with things like preload that learn what you use most and "preloads" the programs before you log in, it can seem that way over time... but in truth it will run just as fast on day one as it does on day thousand so long as misbehaving programs are killed when it's necessary (rare) and you don't try to build your own linux distro, as it were, and not knowing exactly what you're doing.

---

### Post by theozzlives on 2010-01-23
> **d3v1150m471c said:**
> check out "preload". it's in your synaptic package manager. The only problem you might run into with linux getting slower is if you leave your computer running for weeks, maybe even longer, and your cache and ram usage fills up. Solved by restarting.

The Linux Bible states that you can run Linux for extended periods of time without rebooting, unlike Windows. That being said, I run my L.A.M.P. Server 24/7 without rebooting and it runs fine.

---

### Post by JiuJitsu500 on 2010-01-23
But if you never change anything in the server, just run it, of course you never have to restart :)

Normal linux users love the freedom to modify, and seeing the necessity to change their personal computer (like me, all the time) and causing changes, reboots are necessary sometimes. But once done, and everything is runnin the way you choose.... no, reboot aren't really necessary unless the Kernel is changed (like in updates once a month or less). I tihnk there are programs that can upgrade the kernel without haveg to restart too, but I don't use them.

I also don't run a server :)

---

### Post by d3v1150m471c on 2010-01-23
[IMG]http://www.techthrob.com/tech/preload_files/graph.png[/IMG]

---

### Post by JiuJitsu500 on 2010-01-23
I like that chart man :)

But for shizzle, preload is a way cool app, and does everything for you... should be on a list somehwere of optimizing/must-do's when installing Ubuntu (or any debian OS for that matter). All I've found exclude this...

---

### Post by warfacegod on 2010-01-23
The preload description in Synaptic:

preload monitors applications that users run, and by analyzing this
data, predicts what applications users might run, and fetches those
binaries and their dependencies into memory for faster startup times.

Note that installing preload will not make your system boot faster
and that preload is a daemon that runs with root priviledges.

---

### Post by c0mput3r_n3rD on 2010-01-23
One of the biggest problems with windoze speed especially boot time is that it loves letting every single program start up with the O.S!!!!  Run msconfig command and look at the all the startup programs that are ran!  When I fix peoples XP machines, besides defragmenting (about 10x no lie) there drive, and I'll stop no joke about 20 programs from running as well.  It's bad!!

---

### Post by warfacegod on 2010-01-23
That's not so much Windows fault as it is the applications themselves installing with start up privileges by default.

---

### Post by c0mput3r_n3rD on 2010-01-23
Absolutely.  But why would windows give that type of permission to applications like LimeWire, quicktime media player, adware, viruses, spyware, most of them unrecognisable and it wont even give a description or extend the path to see what it actually is!  Madness I tell you.

---

### Post by warfacegod on 2010-01-23
It is crazy. Windows users have been conned into the buy whole "faster" idiocy. Software companies want their products to be quick and peppy and because Windows doesn't lend itself to quality programming, the easiest solution is to tell your software to load itself into the users RAM on boot. And of course MS is going to oblige, everybody gets to make more money that way (see below). That is one of the main culprits in system slow downs and dragging boot times.


Your computer starts getting slow. You buy some "boost" software. Eventually it doesn't work anymore. You buy more RAM or better graphics. Eventually you get so sick of the whole thing that 1 of two things happens.

1. You scrap your install and buy the new Windows OS, where you can start the whole idiot process all over again.

2. You buy a new computer with Windows almost certainly preinstalled, where you can start the whole idiot process all over again.

Option three is, of course, why we're all on this forum in the first place but it almost never happens.

---

### Post by c0mput3r_n3rD on 2010-01-23
> **warfacegod said:**
> It is crazy. Windows users have been conned into the buy whole "faster" idiocy. Software companies want their products to be quick and peppy and because Windows doesn't lend itself to quality programming, the easiest solution is to tell your software to load itself into the users RAM on boot. And of course MS is going to oblige, everybody gets to make more money that way (see below). That is one of the main culprits in system slow downs and dragging boot times.


Your computer starts getting slow. You buy some "boost" software. Eventually it doesn't work anymore. You buy more RAM or better graphics. Eventually you get so sick of the whole thing that 1 of two things happens.

1. You scrap your install and buy the new Windows OS, where you can start the whole idiot process all over again.

2. You buy a new computer with Windows almost certainly preinstalled, where you can start the whole idiot process all over again.

Option three is, of course, why we're all on this forum in the first place but it almost never happens.


Beautifully said my friend.  Where we can profit though, is reinstalling there O.S.'s, upgrading there RAM, cleaning there systems, all while laughing on the inside!! :D

---

