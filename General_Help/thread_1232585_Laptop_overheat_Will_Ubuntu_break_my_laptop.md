---
title: "Laptop overheat? Will Ubuntu break my laptop?"
date: 2009-08-05
forum: General Help
---

### Post by sponsoredwalk on 2009-08-05
Hi i have ubuntu 9.04 on my laptop via wubi and i am worried, i remember years ago seeing messages about ubuntu 6.06 braking due to bugs but they were fixable, and i've checked and found messages about extremely hot laptops using 9.04 but no answer's on how to fix this. I have noticed that this laptop was extremely hot, will it break or will it shorten the lifespan of my harddisk or any component inside? 

Amabo Te. :)

---

### Post by P4man on 2009-08-06
There a few things that might  cause "overheating"; most important one is probably cpu scaling not working; that is, your cpu works at its highest frequency all the time, rather than clocking down when its not being used much. 

In Ubuntu its very easy to check if it works, just right click on a gnome panel, "add to panel", double click on "CPU Frequency Scaling Monitor ". If it tells you cpu scaling is not supported, then you might want to dig further, it may or may not be fixable. (If you have an old laptop, it may not even support cpu scaling, but then the laptop would be designed to run the cpu at 100% speed all the time anyway).

Mind you, even running at the highest frequency, a laptop *should* be designed to cope with that. It would run hotter (and probably louder) than usual and needed, and your batteries won't last as long, but it shouldn't do any real harm to the machine.

Another source of excess heat compared to windows, can be the videocard if you enable compiz eye candy. That will make your videocard work harder, and therefore generate more heat. But no more so (and in fact, considerably less) than for instance a 3D game. It won't cause any damage. If you dont like the battery drain, don't enable compiz ('desktop effects').

---

### Post by burmanabhay88 on 2009-08-06
ubuntu 9.04 tends to heat more than 8.10 atleast. knw that from personal experience. but i have an easy workaround that. I just close all unnecessary processes and services. for eg. i don't use evolution and bluetooth. so i turn them off. you can terminate  these processes using the "System > Administration > System Monitor" and close all unessential services using "System > Administration > Services"
Hope this helps.

---

### Post by sponsoredwalk on 2009-08-06
Yeah i have cpu scaling on, [http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html) is what i used and have it set on conservative. It works at 800MHz, i haven't seen it go up to 1.60 GHz although it still is absolutely roasting, it's not some malfunction with the laptop itself because using vista the laptop is considerably cooler, idk why the laptop is such a great entropy machine using linux and on vista it's standard. Although windows contributes less to the total disorder of the world on my laptop i think it still has a far greater entropic tally in the long run lol.

---

### Post by P4man on 2009-08-07
if you google, you'll indeed find many ppl reporting the same issue, especially with jaunty. Im not sure what causes it, but you could help us find out by running powertop. Open a terminal and type: 
```
sudo apt-get install powertop
```
(or install through synaptic if you want)

then run powertop with:

> sudo powertop

find out how often your cpu is being "woken" and what processes cause it. Powertop will also suggest solutions, though I'd post here before actually doing it.

Another thing to do, first perhaps, is checking what processes, if any, are hogging your cpu. "top" is a nifty program for that.  just run "top" from the terminal.

edit: afterthought. You installed through wubi, does that mean ubuntu shares a partition with windows, and runs on NTFS ? I've seen the ntfs-3G driver goes beserk and hog down my system on ntfs drives with iirc, very small block size. Write performance was also horrible, and cpu would be at 100%. I solved it be throwing windows out of the.. window and converting all my drives to ext, but that may not be the best solution for you :)

---

### Post by burmanabhay88 on 2009-08-07
> **P4man said:**
> if you google, you'll indeed find many ppl reporting the same issue, especially with jaunty. Im not sure what causes it, but you could help us find out by running powertop. Open a terminal and type: 
```
sudo apt-get install powertop
```
(or install through synaptic if you want)


find out how often your cpu is being "woken" and what processes cause it. Powertop will also suggest solutions, though I'd post here before actually doing it.
for you :)

THANKS!!! Powertop's a wonderful tool I used all it's suggestions and my laptop's performance has really really improved.

---

