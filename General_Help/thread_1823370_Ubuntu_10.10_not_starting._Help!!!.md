---
title: "Ubuntu 10.10 not starting. Help!!!"
date: 2011-08-12
forum: General Help
---

### Post by gaurish108 on 2011-08-12
Hi I am running Ubuntu 10.10 on my laptop. Today by mistake I switched off the power supply without shutting down the computer. My laptop battery is dead so I dont use it, and run the laptop only on elctric power supply. 

When I restarted the computer I started getting this strange message on screen.
```

mount:mounting /dev on /root/dev : No such fle or directory
mount:mounting /sys on /root/sys : No such fle or directory
mount:mounting /proc on /root/proc : No such fle or directory

Target filesystem does not have requested /sbin/init
No init found. Try passing init=bootarg

Busybox v 1.15.3(Ubuntu 1:1.15.3-1ubuntu5)
built in(ash)

Enter 'help' for a list of built in commands
(initrafms)

```

I got a terminal prompt with initrafms. where typing 'help' did not really help as it gave me a list of jibberish.

What I am I supposed to do. My hard disk had developed some bad sectors over the past 2 months. 

Could this be the reason?

---

### Post by Kira_Belka on 2011-08-12
mmmm.. your system doesn't mount root file system.. so you need ubuntu  Live-CD at least

---

### Post by kmsalex on 2011-08-12
There's a program that saved my *** a while back, hopfully still in the repose.

```
sudo apt-get install testdisk
```

This of course will have to be done from a live cd, use the most resource light one you've got lieing around.

This is why I've always left batteries in old laptops even if they are crap (i've used many), just so you'll have a few seconds to get the plug back in, or if a power failure do a quick 
```
sudo shutdown -l now
```

If you can access your drives from the live cd in natulase you might be better off just doing a clean install, since your running 10.10 you should probly upgrade to 11.04 (even if its Lubuntu/Xubuntu if you don't care for unity) this is a good excuse for that if nothing else.

Always try to find a silver lining in life:popcorn:

---

### Post by sbraz on 2011-08-12
in short... something VERY bad happened.

> **gaurish108 said:**
> What I am I supposed to do. My hard disk had developed some bad sectors over the past 2 months. 

Could this be the reason?
very probable, yes. maybe cutting the power just struck the final blow. anyway if your drive has bad sectors it means you should seriously consider backing up your data and replace the hdd asap.
why it broke? since it's a laptop i'd say that there is an 80% chance that's a human error: often users forget (or simply doesn't know :) ) that laptops uses mechanical hdds so they just turn it on and toss it around like an old tape player, while there's a tiny magnetic head flying at 50+mph just a few nanometers (or relatively few atoms if you wish) above the disk's platter surface. even just screaming at a hard drive can disturb it's operation. just saying. :)
other causes are overheating, old age... and of course the "maxtor's curse". :D

if you are lucky, you just need to fsck your partitions and you are good to go... on the other hand, if you are not, you might have suffered some major data corruption and in that case i'm not an expert in fixing linux partitions. :(

> I got a terminal prompt with initrafms. where **typing 'help' did not really help as it gave me a list of jibberish**
been there. :(

> **Kira_Belka said:**
> mmmm.. your system doesn't mount root file system.. so you need ubuntu  Live-CD at least
correct. i'd recommend PartedMagic too, it's kind of my swiss army knife. ^_^

---

### Post by gaurish108 on 2011-08-12
Hi friends thank you for your replies. By live CD i assume you mean the original Ubuntu 10.10 installation CD. ? How do I recover my data using this? 

Please let me know some details since I am not really an expert at all this.  :confused: 

Also suppose nothing works out will I have to replace my laptop or just the hard disk?

---

