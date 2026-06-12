---
title: "Windows loading pages faster than Ubuntu using Firefox?"
date: 2010-10-01
forum: General Help
---

### Post by Marzata on 2010-10-01
Two very simmilar laptops connected to the same WiFi router loading the same web pages. Firefox on Windows does that for 3 secons, while Firefox on Ubuntu needs 1-3 minutes to load the same page. What could be the reason for this? Any idea how to fix it? 
The laptop with Ubuntu runs 10.04 LTS (lucid), Firefox is 3.6.10 and on any other WiFi network it loads the web pages really faster but why is much slower than Windows now? 
When testing the speed on [http://www.speedtest.net/](http://www.speedtest.net/) Ubuntu loads times faster than Windows. 
The WiFi router has been reseted. Firefox has been started in -safe-mode, both didn't help. 
Thank you!

---

### Post by dtfinch on 2010-10-01
If you go to the url "about:config", and change "network.dns.disableIPv6" to true, does that make any difference? It's been years since I've had a problem with it personally though.

If it is an IPv6 issue (your router or ISP doesn't support IPv6, but Ubuntu thinks it does), it'd probably affect all of your programs, not just Firefox.  [https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/417757)

---

### Post by Marzata on 2010-10-01
Thank you very much for your answer! This worked great for Firefox! 

How to do the same for the other Internet applications?

---

### Post by lovinglinux on 2010-10-01
> **Marzata said:**
> How to do the same for the other Internet applications?

You can disable it in grub.

See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

---

### Post by Marzata on 2010-10-01
Thank you very much for your answer! This worked great!

---

