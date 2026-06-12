---
title: "System Requirments for Ubuntu 6.06"
date: 2006-06-01
forum: General Help
---

### Post by babumuchhala on 2006-06-01
I have been searching for the past 2 hours in vain so can any one tell me what are the System Requirments for Ubuntu 6.06, and also for Kubuntu 6.06 & Edubuntu 6.06.

---

### Post by nemesa on 2006-06-01
I found this:

[https://wiki.ubuntu.com/DapperReleaseNotes#head-3ce6c302a65d40697613c768ccd0eca28691c7e3](https://wiki.ubuntu.com/DapperReleaseNotes#head-3ce6c302a65d40697613c768ccd0eca28691c7e3)

---

### Post by az on 2006-06-01
[QUOTE=babumuchhala]I have been searching for the past 2 hours in vain so can any one tell me what are the System Requirments for Ubuntu 6.06, and also for Kubuntu 6.06 & Edubuntu 6.06.[/QUOTE]
They are displayed when you boot the cd.

You need a little more than two gigs of hard drive space and 192 Megs of ram.  You can get by with 128 megs of ram using the alternate installer cd.

You will be happy with a Pentium II or better.

---

### Post by Turk on 2006-06-01
My system:
Celeron 2600
256Mb/Ram PC3200
80 Gb/7200
64Mb Intel Extreme Graphics 2 (on board)

I used Hoary and later Breezy and the latest beta' of Dapper, but only progress in performance I see was a little boost (about 3-5% each release), not yet an acceptable speed and workstation.

I also used other environments: Xfce, Enlightenment, ... no difference.

What can be the problem? The DMA is on...

---

### Post by garyng on 2006-06-01
Assuming you want the GNOME desktop, a typical day to day usage system would be :

2G for root(well 1.4 on my system but some slack is always better)
256M+ RAM(less than that you would begin to hit the swap frequently)
500Mhz+ CPU

---

### Post by Turk on 2006-06-01
And only 165 mb of my ram is in use, 25 mb in swap.

---

### Post by garyng on 2006-06-01
My observation is based on my typical usage, firefox alone can grab 100M+ as time goes by and to me, a browser is almost a must for a desktop nowadays.

---

### Post by Turk on 2006-06-02
Firefox is not the problem, if I have nearly 100Mb/Ram free and it's slow, that means there is really something wrong.

---

### Post by remusus on 2006-06-02
My Firefox was taking up 1.3GB of RAM the other day.  Don't know what was up, but it hasn't happened since.

---

### Post by ericesque on 2006-06-02
firefox is know for being plagued by memory leaks.  The longer you have it open and the more you do while it's open, the more memory it's going to hog-- even if you close tabs.  Best thing to do is to close all instances of firefox to eliminate the accumulated waste of memory.  

System specs:  try the live cd.  If it runs decently there, you'll have no trouble with a full install-- you can expect it to run a bit faster.

---

### Post by lapsey on 2006-06-02
I do agree that min specs should be on or near the ubuntu.org front page

---

### Post by missmoondog on 2006-06-02
of my 5 boxes, the oldest/slowest one is an hp6736, intel celeron 667mhz with 384mb's memory. i have it running gnome. seems a little laggy here and there, but tolerable.

---

### Post by FredB on 2006-06-02
[QUOTE=ericesque]firefox is know for being plagued by memory leaks.  The longer you have it open and the more you do while it's open, the more memory it's going to hog-- even if you close tabs.  Best thing to do is to close all instances of firefox to eliminate the accumulated waste of memory.  

System specs:  try the live cd.  If it runs decently there, you'll have no trouble with a full install-- you can expect it to run a bit faster.[/QUOTE]

At least firefox 1.5 ;)

mozilla is working on memory leaks, and trunk builds (very far from being 3.0alpha1 builds) are less leaking ;)

---

### Post by FredB on 2006-06-02
I do agree too.

But I can say that on my P4 2.6 Ghz (3 years old) + 1 Gb of DDRam + 80 Gb HDD + Nvidia GeForce FX 5200, it flies ;)

---

### Post by Turk on 2006-06-02
Also the live cd it works slow, 10-15% than the harddisk based one.

---

### Post by babumuchhala on 2006-06-02
Thank You very much guys. And a special thanks to nemesa for pointing to the exact sys requirments. But I wish they had mentioned the minimum processor speed requirments.

Well as of it my system wont run Ubuntu 6.06 as i only have 64 MB RAM & P3 733 MHz ](*,) as I have used Ubuntu 5.04 & 5.10 and they lagged heavly so had to jump back to XP :mad: 

I am planning to get a new 256 MB SD RAM and I just wanted to know if that would be enough. Also as it is I dont have a CD burner ](*,) so will have to wait abt 2 weeks till i receive those CDs via ShipIt.

As for the bowser I do prefer Opera, mainly because of memory leaks and a lil lack of feature, but I dont want to get this thread hijacked with Firefox v/s Opera or with FF got mem leaks and stuff.

Note: Please dont recommend buying a new PC because its not on the cards till about Feb '07.

---

### Post by Buzzygirl on 2006-08-08
I just came across this thread tonight. 

Background: I have a computer that is running Warty Warthog right now, with no dual boot to Windows. The machine has a 700 MHz Celeron processor and 20 GB of hard disk space. I don't plan to use this computer as a dual-boot system with Windows.

I finally received my 6.06 Dapper Drake CD today. Checking the minimum specs for its install, I see that computers need at least 256 MB of memory to run the graphic installer.  My computer has only 128 MB of memory on it now, so, my next task is to get another 128 MB of memory (at least). I plan to install more memory on the system tomorrow.

Can you Dapper Drake gurus can tell me if I can run DD 6.06 successfully on a 700 MHz processor? Super-speed isn't really a critical issue for me, since I'll mainly be using the computer for Internet browsing, word processing functions, and maybe one or two other applications that are not related to games, video/image processing, or any other truly memory-critical applications.

Thanks!

---

### Post by babumuchhala on 2006-08-08
Well I am running Ubuntu 6.06 on a P3 733 MHZ with 320 MB RAM.

The processing power is quite sufficient, but it the RAM that you will need.

Just install 6.06 and see it for urself or maybe just Run the Live CD (but the performance wont be like the installed version)

My Advice, get a 256 MB RAM chip (I got one here in India for $30 ie a 256 MB SD RAM)

---

### Post by chaosgeisterchen on 2006-08-09
Why not trying Xubuntu? I experienced it to be a big bit faster than the GNOME-Distribution.

---

### Post by JSVH on 2006-08-09
I am running 6.06 on a PII 400MHz with 256mb RAM and a 10 GB hard. I have been useing it daily for about a month and a half. And it has become my primary computer since I sold my laptop for parts three weeks ago. 

I have had almost no problems except for 3D, which is basiclly unusable. But that is probably because I have not been able to get the video card to work. But it is *very* useable. Right now I am listing to music while using multiple tabs in firefox. No lag in the music, or noticable slowdowns in firefox. Well done Ubuntu, you have converted me from an exlusive Windows users to an exclusive Ubuntu fanatic in 6 months.

-John

---

### Post by louieb on 2006-08-09
I have ubuntu on two older computers.
Ubuntu 5.
P1 200 
4.0 gig hd and 3.7 gig hd
128mb edo memory
Ubuntu5, Xubuntu5 and DSL desktops
This machine is slow but serviceable for surfing the Internet and for use as a web and FTP server for my home network. No  noticeable difference in speed between DSL and UBUNTU.
and
PII 400 
two 30 gig hdds
384 mb PC100 memory
Ubuntu 6, Fedora 5 and Win XP home desktops.
Ubuntu runs very well on this computer and is noticeably faster that Fedora and XP. This machine works very well for day to day computing use but it doesn't have enough memory for gaming. Gimp and Paint shop Pro run but they are slow lots of swapping to disk.  
 I use Ubuntu for LAMP development (linux,apache,mysql). Fedora is just there, I was testing it for LAMP development use, but it is just a little to much on the cutting edge. Things don't always work.  When i get the time Fedora will be replace by something else. I use XP when I need to work with Visual Basic 6 it is ok for that. But it is slow when running Paint Shop Pro.

---

