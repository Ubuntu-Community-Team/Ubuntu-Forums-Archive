---
title: "What are all these connections?"
date: 2009-09-05
forum: General Help
---

### Post by t0p on 2009-09-05
Today my internet connection is slower than normal.  I decided to run netstat to try and see what's up.

Check out the attached partial output of **netstat -a**

Why are all these computers connected to mine?  I'm not running a bittorrent client.  The only internet app open (to my knowledge) is Firefox, and I have only 2 windows open - this site and [Scroogle Scraper]("https://ssl.scroogle.org/").

I'm rather baffled by this.  The only thing I've done is connect a new external hard drive, and I don't see how that could be responsible.  Also, I'm using my cellphone to connect my computer to the internet, so I'm behind my mobile service provider's firewall and connections can only be initiated by me (well, it should be like that anyway).

Can anyone tell me what's going on?

---

### Post by Brandon Williams on 2009-09-06
Run netstat like this:
```
sudo netstat -ap
```

The output will tell you which program is associated with each of the established sockets, as well as the pid of the process.

---

### Post by NoaHall on 2009-09-06
Alot of them look like it's tor. Tor uses multiple connections to "spoof" your computer's address through. Tor is also the reason why your network is slow.

---

### Post by uylug on 2009-09-06
Most of them look like websites that you were browsing. Close firefox, wait a couple minutes and run netstat again.

---

