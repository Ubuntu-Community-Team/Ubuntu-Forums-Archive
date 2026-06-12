---
title: "Have lost Network Manager"
date: 2011-04-01
forum: General Help
---

### Post by Goreygirl on 2011-04-01
Hi All

I'm new to Ubuntu (have version 10.10) and am learning my way around the system and language etc (with the help of these forums, guides etc).

How ever I seem to have lost my Network Manager! It's not listed in my System Preferences (only Network Connections is) so I cannot scan for new wireless signals etc. I only noticed when I was away last week, took my laptop with me. I don't have the little wireless icon in my panel either (that I used to click on to find new networks). 

I have a Dell Inspiron 6400 that runs an Intel Wireless Pro 3945 AGB driver.

Any help (in PLAIN English) would be gratefully received.

Gg

---

### Post by Frogs Hair on 2011-04-01
Hi and Welcome

Right click the panel , select add to panel and add the notification area . There are others that have had this problem and it turned out to be more complex than adding the notification area , so use the forum search.

---

### Post by Goreygirl on 2011-04-01
> **Frogs Hair said:**
> Hi and Welcome

Right click the panel , select add to panel and add the notification area . There are others that have had this problem and it turned out to be more complex than adding the notification area , so use the forum search.

Thanks :D

---

### Post by Enigmapond on 2011-04-01
Hi!

Welcome to the forum. If you open the terminal and copy/paste this:

```
sudo apt-get install network-manager
```

This will install it. When installed, right click on the panel and just add the network manager applet...this will put it back on the panel.

Hope this helps.

Cheers!

---

### Post by Goreygirl on 2011-04-01
> **Enigmapond said:**
> Hi!

Welcome to the forum. If you open the terminal and copy/paste this:

```
sudo apt-get install network-manager
```

This will install it. When installed, right click on the panel and just add the network manager applet...this will put it back on the panel.

Hope this helps.

Cheers!

Hi

I tried the above in terminal and it told me that "network manager is already the newest version"

Adding the notifications alert seems to have worked in that I can now see other wireless networks near to me (apart from my own) but I just don't seem to have the "network manager" application in my preferences list.

---

### Post by Enigmapond on 2011-04-01
> **Goreygirl said:**
> Hi

I tried the above in terminal and it told me that "network manager is already the newest version"

Adding the notifications alert seems to have worked in that I can now see other wireless networks near to me (apart from my own) but I just don't seem to have the "network manager" application in my preferences list.

GOOD! That's good news. You didn't lose it it just played an April Fools on you and hid. Glad it all worked out! As long as you have access to it. No idea why it doesn't show in your applications though...

---

### Post by Goreygirl on 2011-04-01
Cheers :)

---

