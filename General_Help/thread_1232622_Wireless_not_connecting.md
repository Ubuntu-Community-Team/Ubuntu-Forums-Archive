---
title: "Wireless not connecting"
date: 2009-08-05
forum: General Help
---

### Post by Wynne G Oldman on 2009-08-05
Hi. I'm using the 9.04 live CD on my laptop, and I can't connect to my router. I'm on Virginmedia, and to log in, in XP, I enter a password. I get to the stage where it's asking for a WAP key in Ubuntu, so I enter my password, and it won't connect. It's the same with other distro's. What am I doing wrong?

---

### Post by slakkie on 2009-08-05
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Usefull output to give us so we can help you (since our crystal ball is broken):

```

lspci | grep -i network
lsusb | grep -i network 
cat /etc/network/interfaces

```

Also, are you using a network manager? If so, which one and what are the settings.

And post what you have done to resolve the issue. So we know where to start and what to ask. 

Best of luck!

---

