---
title: "Can not enable software center recommendations"
date: 2012-05-25
forum: General Help
---

### Post by Chelidze on 2012-05-25
So yesterday I re installed ubuntu 12.04 and today i noteced that i can not enable recommendations in software center 
 When i start software center and Turn on recommendations nothing appears and after i raster software center it shows the button ,,turn on recommendations" all over again 

 is there a way to fix this
                                 thank you for your time

---

### Post by jon zendatta on 2012-05-25
have you updated?
```
sudo apt-get update && sudo apt-get upgrade
```:KS

---

### Post by raja.genupula on 2012-05-25
try this

```
sudo apt-get install --reinstall software-center
```

---

### Post by Chelidze on 2012-05-25
Thank you for your replays 

> **jon zendatta said:**
> have you updated?
```
sudo apt-get update && sudo apt-get upgrade
```:KS

Did not work mate


> **raja.genupula said:**
> try this

```
sudo apt-get install --reinstall software-center
```

will this delete any installed app ??? 

 I am asking because i do not know i am really new to linux

---

### Post by djmaxie on 2012-05-26
Yes same problem here...
Ubuntu software center cannot receive recommendations....I am trying to turn on recommendations but its automatically turned off..

---

### Post by Derek Karpinski on 2012-05-26
Same here.

---

### Post by raja.genupula on 2012-05-26
> **Chelidze said:**
> Thank you for your replays 



Did not work mate




will this delete any installed app ??? 

 I am asking because i do not know i am really new to linux

That will not going to remove/install any extra apps . that will just do take care of Software-center .

---

### Post by Chelidze on 2012-05-26
> **raja.genupula said:**
> That will not going to remove/install any extra apps . that will just do take care of Software-center .

sadly reinstalling the software center did not fix the bug

---

### Post by effay on 2012-05-31
Same problem here. Even after a full reinstall of Ubuntu. I'm fully updated/upgraded and everything too. Have a Software Center login profile and didn't do anything weird or out of my league that could have jacked it up either.

---

### Post by effay on 2012-05-31
Or maybe our assumption that turning on recommendations populates a Recommendations panel is wrong. Maybe it just affects how your "What's New," "Top Rated," search results, etc... get ranked?

Just a thought...

---

### Post by effay on 2012-05-31
No, [it is supposed to populate a panel]("https://wiki.ubuntu.com/SoftwareCenter/Recommendations"). Hmh.

---

### Post by effay on 2012-05-31
Well there's a [bug report]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/996136") on this so far at least. Hasn't been resolved yet though.

---

### Post by Derek Karpinski on 2012-06-04
Seems to be fixed with the latest Software Center update. :D

---

