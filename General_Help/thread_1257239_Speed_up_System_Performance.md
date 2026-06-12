---
title: "Speed up System Performance"
date: 2009-09-03
forum: General Help
---

### Post by CrusaderAD on 2009-09-03
Can someone drop me some suggestions on boosting the system performance? I installed Ubuntu Jaunty 9.04 on a Dell Dimension E520 and it just seems so slow. I can't figure out why, I thought it would fly on this system.

---

### Post by CrusaderAD on 2009-09-03
I tried moving the desktop effects to its lowest setting, didn't make a difference.

---

### Post by bacardiandwatermelon on 2009-09-03
What is slow, anything in particular firefox? or just ubuntu in general?

---

### Post by CrusaderAD on 2009-09-03
The system in general. Opening just about any major application is slow (firefox, adobe, gimp). Sometimes the screen goes grey cause it's waiting so long.

---

### Post by t0p on 2009-09-03
What are your specs?

---

### Post by CrusaderAD on 2009-09-03
[http://www.dell.com/us/en/dfh/desktops/dimen_e520/pd.aspx?refid=dimen_e520&s=dfh&cs=22&~tab=specstab]("http://www.dell.com/us/en/dfh/desktops/dimen_e520/pd.aspx?refid=dimen_e520&s=dfh&cs=22&~tab=specstab")

It's the bare bones version. No special graphics card, Basic celeron processor.

---

### Post by CrusaderAD on 2009-09-04
Bump

---

### Post by Slim Odds on 2009-09-04
> **raptormanad said:**
> It's the bare bones version. No special graphics card, **[COLOR=Red]Basic celeron processor[/COLOR]**.

That might be a large part of your answer right there.....

---

### Post by jocko on 2009-09-04
> **Slim Odds said:**
> That might be a large part of your answer right there.....
But why would ubuntu run so poorly on a celeron 346 (3.06 GHz, if my googling is correct), when it runs perfectly well on my old athlon 1.86 GHz?

---

### Post by jocko on 2009-09-04
> **raptormanad said:**
> [http://www.dell.com/us/en/dfh/desktops/dimen_e520/pd.aspx?refid=dimen_e520&s=dfh&cs=22&~tab=specstab]("http://www.dell.com/us/en/dfh/desktops/dimen_e520/pd.aspx?refid=dimen_e520&s=dfh&cs=22&%7Etab=specstab")

It's the bare bones version. No special graphics card, Basic celeron processor.
How much RAM?

---

### Post by Exodist on 2009-09-04
> **raptormanad said:**
> Can someone drop me some suggestions on boosting the system performance? I installed Ubuntu Jaunty 9.04 on a Dell Dimension E520 and it just seems so slow. I can't figure out why, I thought it would fly on this system.

2 Things.

1) Download the latest kernel and build your own. Its fairly easy. 
When you do build your own just set your Timer Frequency from 250 to 1000 and your Preemptive level from Voluntary Desktop to Low Latency Preemptive Desktop. Also if you dont run a radio station or have any radio tuner cards. You can safely remove all the Radio driver modules from the Drivers section.

The base kernel is a generic all around compatible kernel. A custom built one for your own system will greatly improve performance.

2) Shutdown any Startup Applications that you dont need like Remote Desktop, etc.. etc.. 
They can be found under System-> Preference-> Startup Applications.


I shaved 10secs off my boot time and in addition my desktop is snappier and seems to run alot faster.

---

### Post by Exodist on 2009-09-04
> **Slim Odds said:**
> That might be a large part of your answer right there.....

Nah thats not the issue. Any 1GHz CPU, sempron or celeron included will run Ubuntu very well.

Do need to see how much RAM you have.
Your basic Ubuntu System run BEST with 1GB or more RAM. 500MB is cutting it close. But 1GB is getting close to hitting the sweet spot where it runs great. 

Also did you setup your SWAP folder when Installing the system or did you use the automated setup? The automated disc partitioning will set up around a 3GB swap by default but if you manually configured your setup you may have forgot it. No swap and less the 1GB of RAM can be performance killers bigtime.

- Exo

---

### Post by CrusaderAD on 2009-09-04
Thanks for the great replies. It's running on that celeron processor with 512 megs of ram. I guess that's the issue? Can you use a usb stick as ram in this case like windows vista does? It's just strange cause I have it running on three identical machines and this is the only one that really give me problems. Maybe it's the user trying to do too much stuff at once?

---

### Post by NoaHall on 2009-09-04
Vista doesn't use it as RAM ( as that's incredibly impossible :D due to far too slow file speed) , it uses it as "Swap" in Linux(Page file memory in Windows) To increase your swap, you need to create a larger swap partition using gParted ( or something similar)

---

### Post by philinux on 2009-09-04
It should run ok but if there's no dedicated graphics card and it's having to use system ram. That would slug the system.

---

### Post by P4man on 2009-09-04
> **raptormanad said:**
> Thanks for the great replies. It's running on that celeron processor with 512 megs of ram. I guess that's the issue?

Find out. Open system monitor and see how much he's swapping.

>  Can you use a usb stick as ram in this case like windows vista does? 

Not quite, but you could use a fast usb stick as swap i guess. Then again, it will wear your stick, and an extra 512Mb RAM is probably as cheap and much faster.

> 
It's just strange cause I have it running on three identical machines and this is the only one that really give me problems. Maybe it's the user trying to do too much stuff at once?


Heh. I dont think you can fault the user for doing too much stuff, Id rather say, perhaps the user doesn't have an adequate machine for his needs ;). 

But Im not sure its that. Perhaps something is wrong with the disk performance. You could try benching it with "bonnie" or check the logfiles for problems with the drive; When running just a couple of apps, 512 MB ought to be enough, if its slowing down then already, then something else is wrong IMHO

---

### Post by StuartN on 2009-09-04
Open a terminal and type "free" to see how much memory is accessible, used and free. Ubuntu is likely to have used over 500 mb before opening any applications and begun to use swap space.

Also check your disk space with "df" to be sure there is at least 15% free on the / and /home partitions.

I am using a Dell Inspiron 1501 with much lower specs (except I have 2 mb ram) under Ubuntu 8.10 and have perfectly acceptable performance.

---

### Post by P4man on 2009-09-04
> **NoaHall said:**
> Vista doesn't use it as RAM ( as that's incredibly impossible :D due to far too slow file speed) , it uses it as "Swap" in Linux(Page file memory in Windows) To increase your swap, you need to create a larger swap partition using gParted ( or something similar)

No, readyboost is not swap. Its *cache*. It uses an USB stick to cache disk reads (and writes?). Flash memory on a usb stick doesnt have faster throughput than a harddrive (typically its even considerably slower), but does have near zero seek time, and therefore its quite useable for caching small files.

Linux has no such mechanism afaik, and while it hardly needs one as it's  much more memory efficient than vista (so more RAM can be used as cache), it would still be nice if someone made it.

---

### Post by NoaHall on 2009-09-04
I was explaining in layman's terms, not in a detailed way - swap and cache are pretty much the same anyway.

---

### Post by P4man on 2009-09-04
> **NoaHall said:**
> I was explaining in layman's terms, not in a detailed way - swap and cache are pretty much the same anyway.

No, they are not. Not nearly. A cache is a read or write buffer, using a fast storage medium (onchip L1/L2/L3 cache, ram, flash) to buffer reads or delay writes to a slower medium (ram, harddisk, optical,..);

Swap is virtual memory. Giving your OS more system memory than it has physical ram, allowing you to run apps that require more ram than you have, or run more apps. Or, in the case of windows especially, freeing up RAM to use as.. harddisk cache :) Therefore they may seem related, but they are very different things.

Anyway, sorry to go offtopic

---

### Post by CrusaderAD on 2009-09-04
Thanks for all the great suggestions. I love this forum! I'll going to try and talk the boss into buying more memory... that seems to be the way to go. I'm running the same Ubuntu version on a far older machine flawlessly, but it has much more RAM.

---

### Post by CrusaderAD on 2009-09-30
Do you guys think running one application with Wine would hog resources?

---

### Post by jward3010 on 2009-09-30
> **Exodist said:**
> 2 Things.

1) Download the latest kernel and build your own. Its fairly easy. 
When you do build your own just set your Timer Frequency from 250 to 1000 and your Preemptive level from Voluntary Desktop to Low Latency Preemptive Desktop. Also if you dont run a radio station or have any radio tuner cards. You can safely remove all the Radio driver modules from the Drivers section.

The base kernel is a generic all around compatible kernel. A custom built one for your own system will greatly improve performance.

2) Shutdown any Startup Applications that you dont need like Remote Desktop, etc.. etc.. 
They can be found under System-> Preference-> Startup Applications.


I shaved 10secs off my boot time and in addition my desktop is snappier and seems to run alot faster.

Not to go off topic but is there any good tutorials for doing this?

---

### Post by jward3010 on 2009-09-30
You're problem could be exacerbated by the use of an onboard Intel graphics chip and the current sluggishness Jaunty is experiencing with Intel graphics which causes the desktop and general X stuff to run badly, the background system will run like stink but you'll never get that impression. There is an easy workaround though. Go to a terminal and type:
```
sudo lspci
```
Post the output here in code tags.

Here's some more info on it:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by dummy910 on 2009-09-30
How many rpm's(etc) is that hard drive spinning @? Most folks overlook this and wonder why their machine is slow as(5400rpm drives are dogs compared to 7200's, dont forget transfer ratings too)

_Check your services too_, as most installs have many running(stealing resources) that you do not need. a great progam-tool for this is called Bum(BootUp-Manager).

To install **Bum** via terminal:```
sudo apt-get install bum

```in gnome it will install into the System>Administrator menu with an icon titled **BootUpManager**.

If your not printing, why have Cups running, or on a desktop system, why have laptop-mode, or bluetooth etc... well ya get the idea.

---

### Post by pawhtiobo on 2009-09-30
Hi :)

You can also change your HD settings for best performance with **hdparm**:

[http://ubuntuforums.org/showthread.php?t=16360](http://ubuntuforums.org/showthread.php?t=16360)

[http://linuxhelp.blogspot.com/2004/12/boosting-your-hard-drive-performance.html](http://linuxhelp.blogspot.com/2004/12/boosting-your-hard-drive-performance.html)

see ya :)

---

### Post by CrusaderAD on 2009-09-30
Thanks for the suggestions. I'll try them out and post any results here. pawhtiobo, I dig your signature :) "Our great depression is our lives."

---

