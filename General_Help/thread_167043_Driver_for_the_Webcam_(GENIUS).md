---
title: "Driver for the Webcam (GENIUS)???"
date: 2006-04-27
forum: General Help
---

### Post by minhaz4u on 2006-04-27
My webcam is Genius VideoCAM series v2...To work with it in UBUNTU which driver should I use???

---

### Post by kingmonkey on 2006-04-27
google leads me to [http://mxhaard.free.fr/index.html](http://mxhaard.free.fr/index.html)

---

### Post by minhaz4u on 2006-04-27
Thanks for the reply ..but I can't understand anything written in it...seems like pro language :???:

---

### Post by MartinG on 2006-04-27
I think you'll need to download and compile from source, using the sources in the spca5xx-source package in the repositories.

---

### Post by minhaz4u on 2006-04-27
Any other ideas??? :neutral:

---

### Post by MartinG on 2006-04-28
Truly, I think compiling is the only way.  A driver like this has to integrate with the kernel, and therefore needs to be tailored to whatever kernel you are running; the developer(s) haven't the time or resources to keep issuing fresh modules for each and every kernel out there.

It's not too hard, actually.  You need the compile tools, source code and kernel headers, and a program called module-assistant which does the hard work.  If you run module-assistant it will take you through the process.

---

### Post by minhaz4u on 2006-04-28
Thanks a lottt **MARTIN G** ... I read your post carefully and searched the forum accordingly... I got all the info about installing spca5xx Driver from this : [http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284)

Thanks again **MARTIN** ;) 

Good Job...keep it up :D

---

### Post by MartinG on 2006-04-28
Thanks.  I've not seen that thread before, when I got my camera I had to work it out for myself the hard way :(  (This was in the days before I moved to Kubuntu.)

Don't forget that you'll need to repeat the process when you upgrade your kernel.  And when/if you upgrade to Dapper as I have, some things will change (e.g. different gcc).

---

