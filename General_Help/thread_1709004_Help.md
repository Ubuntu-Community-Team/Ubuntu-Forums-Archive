---
title: "Help"
date: 2011-03-17
forum: General Help
---

### Post by scphoneguy on 2011-03-17
OK, I had Ubuntu once before on an old IMB thinkpad T21 with everything working but that was a long time ago and I have forgotten. I now have a Dell Inspiron 1525 running XP, Vista, and Ubuntu 10.10. Installed Ubuntu using wubi. I cant get the wireless working, works fine on Windows. I've tried following the instructions on the hundreds of threads I've read on how to get this working with no luck. I keep getting E: Unable to locate package ndiswrapper

I only have access to wireless network so need to get this working. Any help will be appreciated!

Thanks!

---

### Post by TeoBigusGeekus on 2011-03-17
What's your wireless card?
```
lshw -c network
```
Have you looked for restricted drivers from the Admin>System menu?

---

### Post by scphoneguy on 2011-03-17
Bcm4312

---

### Post by bcbc on 2011-03-17
This is a sticky in the networking and wireless subforum.
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

---

### Post by scphoneguy on 2011-03-17
Thank You.....BUT, I found that earlier today. I've searched all thru the Networking and Wireless forums and nothing worked. When I do a search like what is described in that link, I get nothing...it doesnt find anything..

Thanks!

---

### Post by bcbc on 2011-03-17
> **scphoneguy said:**
> Thank You.....BUT, I found that earlier today. I've searched all thru the Networking and Wireless forums and nothing worked. When I do a search like what is described in that link, I get nothing...it doesnt find anything..

Thanks!
If you are trying to download the driver from Synaptic then you'll need an active internet connection (wired obviously since the wireless isn't working). Or download the package using another computer.

If you still have no luck, I'd suggest posting on the end of that thread - likely you'll get lots of experienced help.

---

