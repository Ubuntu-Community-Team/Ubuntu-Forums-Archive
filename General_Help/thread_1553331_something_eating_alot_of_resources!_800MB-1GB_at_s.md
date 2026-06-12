---
title: "something eating alot of resources! 800MB-1GB at startup!"
date: 2010-08-14
forum: General Help
---

### Post by krack3rz on 2010-08-14
i dunno wats up! i start the comp. ubuntu latest and my resources are half gone! heres a copy of my ~$free:

------------------------------------total------------used------------free---------shared--------buffers-------cached
[COLOR="Sienna"]________Mem:_______2061076____1249444_____811632_________0______62492_____341252[/COLOR]
[COLOR="DarkOrange"]-/+ buffers/cache:_______845700____1215376[/COLOR]
[COLOR="SandyBrown"]________Swap:_______2189304__________0_____2189304[/COLOR]

i used System Monitor to see this and i notices there are 2 categories that puzzle me, its "Memory" and "Virtual Memory" and wut I need to know is which is swap and which is my RAM?

"Virtual Memory" always uses up crazy numbers that just don't add up, usually Nautilus in it takes up 450-550MB! but in "Memory" ~150MB (i have to end that process to refresh it a lot, i have 9 partitions mounted on my desktop every login and I have almost no other icons on Desktops -> i have 2 displays that operate as an extended screen but i cant move things from 1 to other)

Firefox-bin uses 800MB-1.2GB for Virtual memory and about 150MB in memory (i have 16-20 tabs open usually, they open pretty fast wen I start firefox [~15 sec])

i have havp (no idea wut this does) that has 17 processes of itself and the same path in each and uses about 130MB in each category of memory and virtual category in Sys Monitor.

:confused::confused::confused::confused::confused::confused:
HELP ME!! [-o<

---

### Post by Smart Viking on 2010-08-14
Memory is RAM, virtual memory is swap. 

We need some more information, how much ram do you have, how much swap do you have? The problem with swap is that it is much slower than normal ram since it is just a partition on the harddrive.

---

### Post by krack3rz on 2010-08-14
but i did say how much i have, wen i printed the $free command from prompt. I have 2GB RAM and 2.1GB SWAP.

also if "virtual memory" is swap then y is swap at 0 and "virtual memory" combined is about 2GB?

---

### Post by bodhi.zazen on 2010-08-14
use the -m flag with free so convert the output to mb

```
free -m
```

I do not see anything unusual in that output.

Linux is not windows and Linux uses RAM very different.

Unused RAM is wasted RAM and you are not using swap at all.

See :

[http://www.cyberciti.biz/faq/linux-check-memory-usage/](http://www.cyberciti.biz/faq/linux-check-memory-usage/)

[http://www.linuxjournal.com/article/2770](http://www.linuxjournal.com/article/2770)

[http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage](http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage)

---

### Post by Rubi1200 on 2010-08-15
bodhi.zazen is right about the output.

Also, you could use either the top program (already installed) or htop (available in the Software Center) to monitor processes and their CPU/RAM usage.

---

### Post by krack3rz on 2010-08-15
thats just at startup, i often have to cold reboot the comp. because it gets stuck, thats wen it uses ~1.7GB SWAP and ~1.9GB RAM

that isn't normal, and I have other users on here tell me startup doesn't even use 400 MB RAM! and i've got > 1GB!!

i disabled everything that I dont use and know wat it is. nautilus still often fails on me and freezes, if it is on for more than 1 min. swap starts filling in as well as RAM for no reason.

:confused::confused:

---

### Post by Strongman332 on 2010-08-15
ok re-download ubuntu make a new cd and start your pc from the cd

check your ram whale you are on the live cd environment. if it is runing with reasonable ram you may need to reinstall

i am only using 1 gig of my 4 gig right now so its not linux's way of handling ram

---

### Post by krack3rz on 2010-08-15
is there a better way than reinstalling from scratch? i got way too mush stuff i cant afford to delete and have no space to allocate it to, no CD or flash not an option - too many GBs...

another fun fact: i often have my flash plugin for google chrome go nuts and use over 90MB of memory and crash sometimes but it really helps end taking it from chrome's task manager.

also some mozilla thing crashes sometimes too

*i usually have 2 browsers open at the same time, i wont use them and the resources keep piling up...i just dont get it! :(

---

### Post by bodhi.zazen on 2010-08-15
> **krack3rz said:**
> is there a better way than reinstalling from scratch?

Yes, installing from scratch, without identifying the problem, is almost certainly futile.

> another fun fact: i often have my flash plugin for google chrome go nuts and use over 90MB of memory and crash sometimes but it really helps end taking it from chrome's task manager.

also some mozilla thing crashes sometimes too

*i usually have 2 browsers open at the same time, i wont use them and the resources keep piling up...i just dont get it! :(

Well, the answer to your question has two parts.

Background : As I indicated in my last post, Linux is not Windows. If you have 2 Gb of RAM you want your machine to use it, to make applications and the entire desktop run and feel faster.

First, your RAM usage on startup is as far as I am concerned normal.

With 2 Gb RAM, why would you want to load only 50 Mb of libs into RAM ? Your system would be sluggish and perform as if you only had 50 Mb RAM.

Instead, you are loading 800 Mb of libs into RAM, and you have sufficient ram to spare.

If you do not understand this , then go back and read the links I gave you.

You can reduce this somewhat by disabling unnecessary services and review your start up applications (do you need bluetooth ?).

You can also reduce this if you do a minimal install and add only those applications you need.

Your problem seems to be some kind of memory leak.

To identify the problem, you will need to use tools such as top and identify the abhorrent application.

The problem could be almost anything, including any third party wireless or video (nvidia) drivers.

See :

[http://www.freshblurbs.com/how-profile-memory-linux](http://www.freshblurbs.com/how-profile-memory-linux)

[http://rimuhosting.com/howto/memory.jsp](http://rimuhosting.com/howto/memory.jsp)

---

### Post by DeMus on 2010-08-15
Now this may sound strange, but is there a way to make Linux use more memory so the system will respond faster?
I have 4 GB of ram and use the 64 bits version of Lucid. When I type free at this moment, with 3 tabs open in Chrome and 1 terminal I see this:

free
             total       used       free     shared    buffers     cached
Mem:       4057712    1305164    2752548          0      31404     684300
-/+ buffers/cache:     589460    3468252
Swap:      2028852          0    2028852

I still have plenty of RAM left. Why not use it?

Another question is:
I did not set any SWAP when installing Lucid. Still I see I have 2GB of SWAP somewhere. The system doesn't use it (used 0) but where is it and how can I switch it off?

---

### Post by bodhi.zazen on 2010-08-15
> **DeMus said:**
> Now this may sound strange, but is there a way to make Linux use more memory so the system will respond faster?
I have 4 GB of ram and use the 64 bits version of Lucid. When I type free at this moment, with 3 tabs open in Chrome and 1 terminal I see this:

free
             total       used       free     shared    buffers     cached
Mem:       4057712    1305164    2752548          0      31404     684300
-/+ buffers/cache:     589460    3468252
Swap:      2028852          0    2028852

I still have plenty of RAM left. Why not use it?

Another question is:
I did not set any SWAP when installing Lucid. Still I see I have 2GB of SWAP somewhere. The system doesn't use it (used 0) but where is it and how can I switch it off?

You can force your system to use more RAM if you load things such as /usr into RAM.

There are how-to's if yo search, here is an over view

[http://beuwolf.wordpress.com/2009/06/22/boot-ubuntu-into-ram/](http://beuwolf.wordpress.com/2009/06/22/boot-ubuntu-into-ram/)

IMO, most desktop users can eliminate swap if they have more then 1-2 Gb RAM, you will likely not use swap.

Honestly though, I doubt you will see much of a performance boost by loading all of Ubuntu into RAM, you can try.

---

### Post by Elfy on 2010-08-15
> **DeMus said:**
> I did not set any SWAP when installing Lucid. Still I see I have 2GB of SWAP somewhere. The system doesn't use it (used 0) but where is it and how can I switch it off?

Find it in sudo fdisk -l 

You can use swapoff -a to turn it off

---

### Post by DeMus on 2010-08-15
> **forestpiskie said:**
> Find it in sudo fdisk -l 

You can use swapoff -a to turn it off

sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8b328b32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          19      145408   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              19        6098    48828416   83  Linux
/dev/sda3            6098       60802   439410688   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8b6e8b6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488384512   83  Linux

sda1: /boot
sda2: /
sda3: /Video
sdb1: /home

No swap partition because I did not make one. What else can be used a sswap area?

---

### Post by bodhi.zazen on 2010-08-15
swap file ?

Look at /etc/fstab

```
grep swap /etc/fstab
```

---

### Post by linux18 on 2010-08-15
> **DeMus said:**
> Now this may sound strange, but is there a way to make Linux use more memory so the system will respond faster?
I have 4 GB of ram and use the 64 bits version of Lucid. When I type free at this moment, with 3 tabs open in Chrome and 1 terminal I see this:

free
             total       used       free     shared    buffers     cached
Mem:       4057712    1305164    2752548          0      31404     684300
-/+ buffers/cache:     589460    3468252
Swap:      2028852          0    2028852

I still have plenty of RAM left. Why not use it?

Another question is:
I did not set any SWAP when installing Lucid. Still I see I have 2GB of SWAP somewhere. The system doesn't use it (used 0) but where is it and how can I switch it off?
linux will always try to run most efficiently, you can turn swap off in gparted right click the swap partition > swapoff

as for krack3rs, it sounds like a memory leak and since lucid was launched there have been three memory leaks (afaik). to fix 2 of them:

- sudo apt-get update && sudo apt-get --fix-broken upgrade 

then backup your firefox profile and:

- sudo apt-get purge firefox* && sudo apt-get install firefox

normally I also:

- sudo apt-get clean

just to purge old caches, but it won't be necessary to fix your memory leak
I've got compiz, rgba, firefox + 20 tabs, and no swap with ram usage < 550MB

---

### Post by DeMus on 2010-08-15
> **bodhi.zazen said:**
> swap file ?

Look at /etc/fstab

```
grep swap /etc/fstab
```

Nothing, as I expected because I did not set any swap in my system.

---

