---
title: "low internet download speed"
date: 2010-06-11
forum: General Help
---

### Post by star11786 on 2010-06-11
i m new to ubuntu (just installed it one week ago)
ubuntu version 10.04

until day before yesterday, everything is working fine but now specific problem arises that is my internet download become 1/4th than usual.

heres the story:
i have internet (LAN) connection of 512 kbps. when i tries to download anything, using (syneptic, firefox default downloader, jdownloader) the download speed i get is 10-20 kb/s which should be 50-60 kb/s. the limited downloading speed is only when i tried to download a file; browsing n online video content play at max. speed i.e. 50-60 kb/s. i m using net speed panel applet to monitor current net speed.

n here is something unexpected:
during downloading, when i start a game(openTTD or battle of wesnoth), downloading speed accelerated to max. (50-60 kb/s) but when i close the game, it drop back to 10-20 kb/s. so definitely this isn't the problem with the net.

can anyone tell me, where's the problem??

---

### Post by Peter09 on 2010-06-11
Just to check....
can you tell us the figures again but take note that 10kB and 10kb are different. A capital B means bytes and a small b means bits. A network running at 10kB is around 10 times faster (approx) than one running at 10kb. 
 
The only real way to check your speed is to go to a site that will do that - for instance
 
[http://www.speedtest.net/](http://www.speedtest.net/)
 
Variations in speed occur for may reasons.

---

### Post by dcstar on 2010-06-11
> **star11786 said:**
> i m new to ubuntu (just installed it one week ago)
ubuntu version 10.04

until day before yesterday, everything is working fine but now specific problem arises that is my internet download become 1/4th than usual.
........
n here is something unexpected:
during downloading, when i start a game(openTTD or battle of wesnoth), downloading speed accelerated to max. (50-60 kb/s) but when i close the game, it drop back to 10-20 kb/s. so definitely this isn't the problem with the net.

can anyone tell me, where's the problem??

Add the CPU scaling applet to a panel and check if your CPU is running at 100% when it works correctly.

---

### Post by star11786 on 2010-06-11
> **Peter09 said:**
> Just to check....
can you tell us the figures again but take note that 10kB and 10kb are different. A capital B means bytes and a small b means bits. A network running at 10kB is around 10 times faster (approx) than one running at 10kb. 
 
The only real way to check your speed is to go to a site that will do that - for instance
 
[http://www.speedtest.net/](http://www.speedtest.net/)
 
Variations in speed occur for may reasons.

in windows world, kbps stands for kilobits per sec and kb/s stands for kilobytes per sec. i have mentioned kbps only for my connection speed, n on everywhere else i had used kb/s

my problem i get the DOWNLOAD speed of 10-20 kb/s which should be 50-60 kb/s. n if i turned on a game (openTTD or battle of wesnoth), i get normal download speed (50-60 kb/s) but which turn off the game, speed drops back to 10-20 kb/s.

TEST RESULTS are 0.54 Mb/s 

but again i had already mention that browsing speed is normal

but when downloading a file (like through synaptic or even with firefox default downloader), i get decreased speed. . .

---

### Post by star11786 on 2010-06-11
> **dcstar said:**
> Add the CPU scaling applet to a panel and check if your CPU is running at 100% when it works correctly.

ok i just checked it, when i open openTTD in window mode, CPU is running between 60-70%, but i got normal download speed as far as openTTD is running. . .

---

### Post by dino99 on 2010-06-11
try with an other DNS like 8.8.8.8 (google) into /etc/hosts:

nameserver 8.8.8.8 google

---

### Post by muteXe on 2010-06-11
Interestly, since installing lucid i'm having crap download speeds as well (75%ish slower than when i had hardy installed). Sometimes the pages fail to load and I have to F5 to get them to reload. (i have a slackware partition on the same machine that is fine in terms of DL speed).
I will be interested to see the replies in this thread.

---

### Post by star11786 on 2010-06-11
> **dino99 said:**
> try with an other DNS like 8.8.8.8 (google) into /etc/hosts:

nameserver 8.8.8.8 google

can u please elaborate what should i do??
as i m not into networking so i don't know much about it, n nothing at all about linux beside basics

---

### Post by star11786 on 2010-06-11
> **muteXe said:**
> Interestly, since installing lucid i'm having crap download speeds as well (75%ish slower than when i had hardy installed). Sometimes the pages fail to load and I have to F5 to get them to reload. (i have a slackware partition on the same machine that is fine in terms of DL speed).
I will be interested to see the replies in this thread.

well if u got the same problem then try to install openTTD(available through synaptic). n then run the game(it will run in window mode). then download something n see if the download speed become normal.

if it does then u got the same problem as mine, n it will confirm i m not the only one having that problem

---

### Post by star11786 on 2010-06-12
anyone got any idea about my problem???

---

