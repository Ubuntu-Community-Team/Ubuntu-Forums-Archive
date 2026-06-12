---
title: "KDE4 uses one entire core , why?"
date: 2011-05-25
forum: General Help
---

### Post by FrostBlue on 2011-05-25
Hi,
I have two truecrypt volumes which I usually load and once I do my cpu usage peaks in the graph. After I exit truecrypt , System Monitor shows two KDE4 running , each using 50% cpu.

The only way to get out of this is to restart.

Does anyone know why this happens ?

---

### Post by FrostBlue on 2011-05-28
Okay this is not just with truecrypt , KDE4 goes rogue and eats up most of the cpu,the graph just never comes down. Even if I boot up the machine and nothing is running. I am on Maverick , should I go to Natty ?

---

### Post by wildmanne39 on 2011-05-28
> **FrostBlue said:**
> Okay this is not just with truecrypt , KDE4 goes rogue and eats up most of the cpu,the graph just never comes down. Even if I boot up the machine and nothing is running. I am on Maverick , should I go to Natty ?

Hi, going to natty is up to you,some people have had problems with natty doing things close to that, have you enabled desktop effects if so turn them off and see if that helps. You can install top and see what process is causing the problem if is is just one.

---

### Post by FrostBlue on 2011-05-28
Yes I have effects on usually as it seems that windows respond faster with the effects otherwise there a noticeable lag. I always thought the opposite should be true. Don't know whats going on but I will try and see.

Thanks for replying.

---

### Post by FrostBlue on 2011-06-01
Looks like Nepomuk was the culprit. I had forgotten to keep it disabled. Now things seem a bit more stable. No need for Natty yet. Am going LTS to LTS this time.

---

### Post by mastablasta on 2011-06-01
problem with LTS is that it has older version od KDE which is much less stable and has quite a few bugs. If problems persist upgrading to latest KDE (using PPA) might be an option. Upon (only) KDE upgrade i enjoy improved system performance. everyhting runs more smooth and also a couple of bugs were sorted out and a few minor yet noticable improvements made (in menues).

---

### Post by FrostBlue on 2011-06-01
Thanks Mastablasta,
Yes I always have the latest KDE from launchpad but I also had backports turned on and didn't exactly know where this problem came from. Sometimes some updates mess things up , you just never know. After going through a bad experience with Intrepid I am sticking to a stable release until the next stable one. I just choose what updates I want carefully on my production machine.

---

