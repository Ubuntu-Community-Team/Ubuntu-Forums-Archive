---
title: "A problem"
date: 2009-11-16
forum: General Help
---

### Post by Denton Larson on 2009-11-16
Hi everyone

I have a problem I would like some assistance with.
I have Ubuntu 9.04.
There is a page [http://www.goes.noaa.gov/GSSLOOPS/ecir.html](http://www.goes.noaa.gov/GSSLOOPS/ecir.html)
That I like to look at. At one point I had it going  
Then I was going to upgrade to 9.10, BIG mistake. 
After I re-formated the drive I got it in there, but it was SLOW. 
So I re-formated the drive again and have 9.04 in the drive now.
I have had something I copied in the terminal but have lost it.
There is a loop in the pictures I look at, now it is a grey screen.

Can anybody help me? 

Denton Larson
WB0ZUR

---

### Post by cenzorrll on 2009-11-16
try installing flash.

```
sudo apt-get install flashplugin-nonfree
```

that should do it. or you can go through synaptic and search for that package

---

### Post by Denton Larson on 2009-11-18
> **cenzorrll said:**
> try installing flash.

```
sudo apt-get install flashplugin-nonfree
```

that should do it. or you can go through synaptic and search for that package

I installed the package, but it is the same.

Denton

---

### Post by mechro on 2009-11-18
Try **adobe-flashplugin** via Synaptic.

If you're using Firefox you may have to reconfigure its plugin paths.

---

### Post by sgosnell on 2009-11-18
It works for me.  It's definitely a flash problem if it won't work, because that site uses flash for the animation.  Can you play other flash videos, such as YouTube, etc?  

I suggest installing the real Adobe player.  Go to [http://www.adobe.com](http://www.adobe.com), click on the Get Adobe Flash Player, and select the .deb version, download it and install with gdebi.

---

