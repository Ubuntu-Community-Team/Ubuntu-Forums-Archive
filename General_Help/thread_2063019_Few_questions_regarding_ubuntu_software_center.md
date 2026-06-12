---
title: "Few questions regarding ubuntu software center"
date: 2012-09-26
forum: General Help
---

### Post by sorabh.v6 on 2012-09-26
I have two questions regarding it:
1>How can i install two or more softwares paralelly as i used to in windows .
2>Software download speed of it is very slow it doesnt even utilises 50% of link speed.
What should i do to sort out above problems.
Thanks in advance.

---

### Post by HiImTye on 2012-09-26
1) start installing one, and then start installing another
2) that's an issue with either the server speed or another network issue. try a different server

---

### Post by shaktiman1234 on 2012-09-26
The very way ubuntu works you won't be able to install two packages simultaneously.
if you try you will get this in terminal.
```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
Ubuntu software center inherits this problem.
So it queues all the installation requests. That is not so bad.

---

### Post by jerrrys on 2012-09-26
> **shaktiman1234 said:**
> The very way ubuntu works you won't be able to install two packages simultaneously.
if you try you will get this in terminal.
```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```Ubuntu software center inherits this problem.
So it queues all the installation requests. That is not so bad.

Thats saying you have more than one package manager open.  Maybe the software center and trying to use apt-get.

You should be able to click on as many package downloads as you want in the software center.

I do not use this method myself.  I prefer more control that [synaptic package manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en") offers.

---

### Post by HiImTye on 2012-09-27
> **jerrrys said:**
> Thats saying you have more than one package manager open.  Maybe the software center and trying to use apt-get.

You should be able to click on as many package downloads as you want in the software center.

I do not use this method myself.  I prefer more control that [synaptic package manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en") offers.
he was addressing using multiple package managers (or rather, multiple copies of the same package manager). Software centre installs consecutively, rather than concurrently for this reason, as it is mostly just a front end for apt.

personally, I prefer to use aptitude + apt-get/dpkg to any of the graphical managers, but they are there for people who are less comfortable in the terminal

---

