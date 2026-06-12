---
title: "LogMeIn is a no go...any other recommended services?"
date: 2010-06-08
forum: General Help
---

### Post by at0msk on 2010-06-08
I like to remote into my home pc's over LogMeIn but it appears that there's no way to configure that for Ubuntu.

What's the common or most accepted recommendation? :confused:

---

### Post by at0msk on 2010-06-08
I was just wondering why I'd not heard anything given all of the activity on the forums then I looked at the first page and found that my thread had been bumped all the way to page 2 (or farther)! :D Wow. I can't believe with all of the activity not ONE person can stop by and give their 2 cents.

---

### Post by _khAttAm_ on 2010-06-08
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by at0msk on 2010-06-08
> **_khAttAm_ said:**
> [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

Thanks. We use VNC at work within a Windows environment so I will give the steps here a try at home.

---

### Post by at0msk on 2010-06-08
Ah, so it seems that I'd need a public key for each pc I'd remote from then?

---

### Post by howefield on 2010-06-09
Have a look at Teamviewer, who have recently released a Linux version, albeit it is in Beta and runs via wine, but seems to work very well.

---

### Post by at0msk on 2010-06-09
> **howefield said:**
> Have a look at Teamviewer, who have recently released a Linux version, albeit it is in Beta and runs via wine, but seems to work very well.

Thanks for the heads up. That looks interesting. Might you know if I could install that on the laptop and leave it running so that I could connect to it any time?

Dang it I just hope LMI gets out of box support for ubuntu soon. :\

---

### Post by howefield on 2010-06-09
> **at0msk said:**
> Might you know if I could install that on the laptop and leave it running so that I could connect to it any time?

Yes you can, quite easily.

You don't say which operating system you are connecting to, but teamviewer is cross platform in that it can connect between linux, mac and windows systems.

---

### Post by cj66 on 2010-06-09
I agree. TeamViewer is the best choice. Its free for personal use and works fine even when I control 3 computers with different OS [Ubuntu x2, XP] using my host PC.
It works like a charm!

---

### Post by efflandt on 2010-06-09
They do have a LogMeIn client that I used in 9.10 (have not tried it in 10.04).  But it is 32-bit only.  I got it to half work in 64-bit by configuring nswrapper for its plugin (it brought up the menus in the browser), but it did not show the remote display (probably stumbled trying to use 64-bit Java).

It did work fine in 32-bit 9.10.

Of course if you are connecting "to" another Linux box, you can either use ssh with X11Forward enabled to run X programs remotely, or VNC.

---

