---
title: "Navigating a directory in ndiswrapper?"
date: 2012-03-15
forum: General Help
---

### Post by SystemsGO on 2012-03-15
I finally fixed my issues with Ndiswrapper, I was able to update to version 1.57. :D Now I need to install my driver. 

I put the drivers in my home folder in a folder called "Wifi-Drivers". Here is the command I'm running, please correct me if I'm wrong. 

 ndiswrapper -i ./Wifi-Drivers/bcmwlhigh5.inf

It returns the following error:  couldn't open ./Wifi-Drivers/bcmwlhigh5.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.


Am I simply making a mistake where I'm directing my installation? If so, can anyone help?

---

### Post by SystemsGO on 2012-03-15
anyone?

---

### Post by SystemsGO on 2012-03-15
I tried entering the command # ndiswrapper -l Just to see if it may have installed anything, it seems to not be doing anything. So then I did the modprobe command, it also does nothing? What's going on?

---

### Post by SystemsGO on 2012-03-15
I fixed it, and got my NWA3100 working quite successfully.


Thanks not helping me whatsoever, guys! Much appreciated.

---

### Post by jerome1232 on 2012-03-15
> **SystemsGO said:**
> 
Thanks not helping me whatsoever, guys! Much appreciated.

Generally wait 24 hours to bump your own thread, sometimes it just takes some time for people with relevant info to see your thread, patience is a must, forums aren't always a super fast way to get answers. Remember we are all here on our own time to help each other out.

I was about to post and saw that you already figured it out, glad you finally got it working!
btw you refer to your own home as ~/ so it should've been

```
ndiswrapper -i ~/Wifi-Drivers/bcmwlhigh5.inf
```

You can also drag a file onto your terminal and the full path to it will be copied in there.

Anyways glad you finally got it working!

edit: I believe you need to just load the driver at login.

The bottom of this guide should help. look for the "Automatically load at startup" section

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by SystemsGO on 2012-03-15
> **jerome1232 said:**
> Generally wait 24 hours to bump your own thread, sometimes it just takes some time for people with relevant info to see your thread, patience is a must, forums aren't always a super fast way to get answers. Remember we are all here on our own time to help each other out.

I was about to post and saw that you already figured it out, glad you finally got it working!
btw you refer to your own home as ~/ so it should've been

```
ndiswrapper -i ~/Wifi-Drivers/bcmwlhigh5.inf
```

You can also drag a file onto your terminal and the full path to it will be copied in there.

Anyways glad you finally got it working!

edit: I believe you need to just load the driver at login.

The bottom of this guide should help. look for the "Automatically load at startup" section

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Thank you so much for that. It now starts on startup. ^_^ It's working quite stable. I've read from many who tried doing it with this specific card that it's unstable, but mine is completely stable it seems. I'll continue to test it though.

---

### Post by reazonnecrext on 2012-03-18
[http://www.playblackjackonline2012.com](http://www.playblackjackonline2012.com) , play blackjack online vegas , 3219342329 , [play blackjack online real]("http://www.playblackjackonline2012.com") , 1317329518 , [play blackjack online multiplayer](http://www.playblackjackonline2012.com) , 1990811405 , [http://fortlauderdalefloridahotels.weebly.com](http://fortlauderdalefloridahotels.weebly.com) , cheap hotels near fort lauderdale beach , 9186091211 , [cheap hotels in fort lauderdale fl]("http://fortlauderdalefloridahotels.weebly.com") , 1207149307 , [cheap hotels in fort lauderdale fl](http://fortlauderdalefloridahotels.weebly.com) , 4807029690 , [http://www.bestvodka.org.uk](http://www.bestvodka.org.uk) , best vodka for jello shots , 2155554659 , [best vodka world 2011]("http://www.bestvodka.org.uk") , 2597891760 , [best vodka under 50](http://www.bestvodka.org.uk) , 6684891175 , [http://www.quicktrim2k.info](http://www.quicktrim2k.info) , quicktrim fast cleanse 48 hour reviews , 3193714343 , [quicktrim iso-flush]("http://www.quicktrim2k.info") , 1543754695 , [quick trim 14 day cleanse directions](http://www.quicktrim2k.info) , 3435515743

---

