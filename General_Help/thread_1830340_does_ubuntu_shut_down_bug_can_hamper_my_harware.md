---
title: "does ubuntu shut down bug can hamper my harware?"
date: 2011-08-21
forum: General Help
---

### Post by vikash_chandola on 2011-08-21
hello!!
Ubuntu does not shut down by itself. As i click shut down. instantly black screen appear and last it is written **system halted**, Nothing happen after that. actually all this take less than 3 seconds. I think it is too less time for all service to be closed. (as compared t windows). I fear that something happening wrong in background. Is everything happening correctly. 
what should i do?

OR

it is normal just continue with this problem. press shut down button on CPU after shut down.


give me terminal commands to shut down computer. that may help.

---

### Post by cgroza on 2011-08-21
The shutdown time of Ubuntu is very short. You don't need to worry about it.
On my Arch installation and Ubuntu, I use:
```

sudo halt now

```
And this shuts down my computer.

---

### Post by Topsiho on 2011-08-21
Ubuntu shuts down much faster than Windows. Very much faster. But this still depends on the speed of your computer. My desktop shuts down in almost no time at all, while my netbook takes some time doing so.

Topsiho

---

### Post by jfed on 2011-08-21
If what cgroza said didn't work, try one of these.

```
sudo shutdown -h now
```

or

```
sudo shutdown -r now
```

hope this helped!

---

### Post by vikash_chandola on 2011-08-21
> **Topsiho said:**
> Ubuntu shuts down much faster than Windows. Very much faster. But this still depends on the speed of your computer. My desktop shuts down in almost no time at all, while my netbook takes some time doing so.

Topsiho
My system specs are 
Intel Pentium 4 ;2.7 GHz processor.
1GB DDR2 RAM
integrated graphic card.(I can't run KDE, GNOME 3 etc , use Ubuntu classic)
others.......

Are these good enough to close computer within 4 seconds.

Bow i am feeling better after hearing that it(shut down problem) will not do anything bad.

---

### Post by Primefalcon on 2011-08-21
hmm what I've always used to shut down is 

```
sudo shutdown -P now
```

that is of course unless you dont want your system powered off

for more info on the shutdown command btw... just type in the following

```
man shutdown
```
just remember you have to precede any shutdown command with sudo

FYI Windows while fairly quick to bootup has an unreasonably long shutdown time IMO....

---

### Post by Topsiho on 2011-08-22
> **vikash_chandola said:**
> My system specs are 
Intel Pentium 4 ;2.7 GHz processor.
1GB DDR2 RAM
integrated graphic card.(I can't run KDE, GNOME 3 etc , use Ubuntu classic)
others.......

Are these good enough to close computer within 4 seconds.

Bow i am feeling better after hearing that it(shut down problem) will not do anything bad.

Possibly. I couldn't tell you exactly. But the specs are not bad at all. It also depends I think on how many applications are running. But I don't think you have to worry.

Topsiho

---

