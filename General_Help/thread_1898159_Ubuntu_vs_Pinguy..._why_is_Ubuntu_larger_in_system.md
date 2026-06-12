---
title: "Ubuntu vs Pinguy... why is Ubuntu larger in system"
date: 2011-12-20
forum: General Help
---

### Post by bluexrider on 2011-12-20
I have 2 installations of 11.04 on the same HDD. One is Ubuntu the other is Pinguy. They both have the same basic applications installed from the CD.

Now Pinguy comes with a lot of extras like XBMC, Handbrake and DeVeDe; all the bells and whistles but the Ubuntu installation is far greater in size than that of Pinguy.

Compare Ubuntu 28.8Gb to Pinguy 9.45Gb and the Home directories are duplicated. 

Where does the bloat come from? Or whats not in Pinguy that should be?

Can I trim Ubuntu and not break it?

---

### Post by xyzzyman on 2011-12-20
28.8GB's on Ubuntu? Do you have a /home partition? You may have temp files built up somewhere's. Take a look at bleachbit. Run it as root and as a regular user. Be careful not to wipe out your firefox/chrome history if they are important to you. Hopefully there's cache files or some old log files sitting around that built up. Once we find out why you're 4-5x bigger than you should be (If you had a reason to be usign 28GB's for just the OS and applications you'd know it), we can take a look at installed packages because I usually wind up removing 500MB-1GB of packages that are pre-installed by default.

---

### Post by bluexrider on 2011-12-20
> **xyzzyman said:**
> Do you have a /home partition?

If you mean does the /Home reside within the same partition as Ubuntu --YES-- 

> **xyzzyman said:**
> You may have temp files built up somewhere's. Take a look at bleachbit. Run it as root and as a regular user.

I 'am using Pinguy 99% of the time therefore no temp files or log files larger than 10.0Mb

Not sure here but I can remember a recovery issue a couple of months back. Guess will look for additional logs of data elsewhere.

---

### Post by xyzzyman on 2011-12-20
Baobab (Disk Usage Analyzer)is installed by default. Maybe you'll get lucky and find a 15GB directory or file. I've had multi gb log files before while something was crashing/restarting repeatedly. I've also had 3+ gigs in google chrome cache in no time. 

Even though everyone's install is different and my /home is on it's own partition, my Ubuntu install is 4.59GB's and it's my daily use OS.

---

