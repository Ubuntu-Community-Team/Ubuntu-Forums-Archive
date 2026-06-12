---
title: "Avant Window Navigator"
date: 2011-03-04
forum: General Help
---

### Post by Arminius on 2011-03-04
I tried to post this on the AWN forums but they seem to be faulty.

does anyone know if there is a 3rd party applets that just shows what hard drives are mounted?
even better one that shows unmounted drives as faded and mounted ones as non faded?

the reason I need this is that my conky's are burying my hard drives on the desktop.

---

### Post by Frogs Hair on 2011-03-04
The awn-applets-core package in the software center includes plugger , an applet that displays volumes , but it's written in C.

---

### Post by Arminius on 2011-03-04
I've googled around, but I can't find the awn-applets-core package or the AWN software center, so if you could point me in the right direction as to how to find that package I would be in your debt.

---

### Post by Frogs Hair on 2011-03-04
First of all I am using 10.10  and  I found the package in the software center. and Plugger was described in the More Info details

---

### Post by Frogs Hair on 2011-03-04
This is what I found , I meant to add this in the previous post.

---

### Post by Arminius on 2011-03-04
ahh the ubuntu software center
I'm retarted
and yet when I tried to install it I got
"This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time"
so still not quite there, if anyone has the patience to help?

---

### Post by Frogs Hair on 2011-03-04
You may need to add the Awn PPA to get that package to work , but I'm not sure. 
[http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html](http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html)

---

### Post by Arminius on 2011-03-05
I'm afraid that didn't solve it, anyone else?

---

### Post by davidmohammed on 2011-03-05
what errors do you see if you type

```
sudo apt-get update

sudo apt-get upgrade

sudo apt-get install awn-applets-c-core

sudo apt-get install awn-applets-c-extras
```

n.b. the above assumes you have NOT installed the ppa.

if you have, you'll need to remove the awn packages first - start synaptic manager and search for awn.  remove all the suggested awn packages.

---

### Post by MacintoshLover on 2011-03-05
Dude, where did you get that skin! Also, AWN was being stupid for me too. I switched to Docky.

---

