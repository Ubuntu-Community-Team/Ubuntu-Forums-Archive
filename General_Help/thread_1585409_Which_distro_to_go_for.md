---
title: "Which distro to go for?"
date: 2010-09-30
forum: General Help
---

### Post by Strategist01 on 2010-09-30
Hi guys

I have an old PC that runs win XP (slowish...) and was my faithful PC for 5 years. Alas, its RAM has degraded and it never had a graphics card to speak of, but it has a nice 1.6GHz CPU and a 80GB HDD. I'm thinking of using it has the network storage server, or just a second backup PC - and I want it as a file server to store my extra stuff.

specs:

RAM: 192MBs (really degraded)
CPU: 1.6GHz AMD KM400
graphics: A graphics chip of 16MBs
HDD: 80GBs

It also has a optical drive capable of reading DVDs and writing CDs (but I'm not so sure on that one) and 6 USB ports...

Which distro should I go for? I was thinking Xubuntu, and I don't want a server edition as me and CLIs are fine but not friends!

Thanks guys.

---

### Post by spiky001 on 2010-09-30
why not upgrade the memory solve the problem

---

### Post by Strategist01 on 2010-09-30
> **spiky001 said:**
> why not upgrade the memory solve the problem

Even though it does have DDR 2 RAM slots I'm not buying anything for it as I'm saving up for a major PC upgrade so I just want to breathe a little bit of life in it before a give it away or something...

---

### Post by msakms on 2010-09-30
I have the exact same specifications as you do. Though, getting a 2GB RAM will boost up your overall performance "noticeably". I'm running   Ubuntu 10.04 (lucid) FTP server and it works like charm.

---

### Post by Strategist01 on 2010-09-30
Ok, does the server edition I can DL from the site have a GUI that I can use?

---

### Post by msakms on 2010-09-30
> **Strategist01 said:**
> Ok, does it have a GUI that I can use?
Sure it does have hell of a GUI XD

---

### Post by slooksterpsv on 2010-09-30
Ubuntu, and even Ubuntu server (current version) would not be a viable option as Ubuntu requires at least 512MB of RAM, and Ubuntu Server requires at least 384MB of RAM.

I would recommend Slitaz. [http://www.slitaz.org/en/get/index.html](http://www.slitaz.org/en/get/index.html)

Even if you could get the Ubuntu Server edition on  your machine, it's text-based only, unless you install a Window manager.

EDIT: Xubuntu requires at least 192MB to run the live-cd. Even thought it will run, it'll be slow as they strongly recommend having at least 256MB of RAM.

---

### Post by snowpine on 2010-09-30
If your RAM is "degraded" then switching to a different distro will not fix it. ;)

With such low specs, and with a home server as your stated goal, I would recommend doing a command-line-only install (sorry) and using something like [Webmin]("http://www.webmin.com/demo.html") as your "GUI" from another machine. 

Since hardware failure is looming, you should probably choose a distro with a long support cycle (so you are not reinstalling every 6 months) such as Ubuntu LTS, Debian, CentOS, etc.

---

