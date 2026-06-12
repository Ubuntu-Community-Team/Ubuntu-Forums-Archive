---
title: "performance"
date: 2010-09-19
forum: General Help
---

### Post by vinay nadig on 2010-09-19
hi, i have been using ubuntu 10.04 for a month now, the initial bootup time was about 17 seconds.. but as time wore on, it has come to 25 seconds. i have installed bootup manager and disabled all the services that i dont need. any help on improving my boot time??

another problem is my system performance.. in the initial days, the OS used to take up about 350 mb of my RAM(i hav a 1 gig ram on my box) but now, even with just a browser running, it takes upto 450 mb.. and my system load peaks upto 2 sometimes with just the browser running  and my cpu starts hyperventilating.. any ideas on optimizing the performance? i use a dual core processor 2.8 GHz.
thnx in advance!! :)

---

### Post by lmarmisa on 2010-09-19
Try to install the bootchart package if you wish to know the detailed times of the boot process:

[https://wiki.ubuntu.com/BootCharting](https://wiki.ubuntu.com/BootCharting)

---

### Post by sikander3786 on 2010-09-19
You can run **top** in a terminal and see which process are using up most of the RAM and processor.

Somtimes flash running in a browsers seems to suck all the RAM and CPU.

See for any processes that you don't expect to be there.

---

### Post by vinay nadig on 2010-09-19
hmm.. i have htop installed and checked it out in the terminal.. looked like a process called clamd was eating up a lot of RAM nad processor time.. a quick googling revealed that it s a AV daemon and not much harm in killing it.. will there be a problem from not running that process?? :?: and also disabled some eye candy effects from compiz.. the sys load has come down to 0.47 now.. :)
and i also installed bootchart.. but couldn't figure out how to use it.. so gonna remove it..
Thnx for the help!! :)

---

### Post by mr_luksom on 2010-09-19
If you are concerned about RAM usage, try Xubuntu. With a Chomium session running, I only use about 120mb of RAM.

---

### Post by vinay nadig on 2010-09-20
> **mr_luksom said:**
> If you are concerned about RAM usage, try Xubuntu. With a Chomium session running, I only use about 120mb of RAM.

hmm.. i googled a bit on RAM usage and learned that linux uses unused RAM as cache memory for frequently used applications and that its a good thing which speeds up the system..
So, the only thing i am worrying about right now is my system load.. right now with just the transmission torrent client and the firefox running, the load is at 1.21. :(
Like u said, i am going to give xubuntu a try.. :)

---

