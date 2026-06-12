---
title: "&quot;b-src is not know on line 2 in source list /etc/apt-sources.list&quot;"
date: 2012-04-29
forum: General Help
---

### Post by kingmetalx on 2012-04-29
I tried to install the "ojno-unity-minimize-on-click" but now I cannot update any packages, load synaptic, or install anything because I get a failed message (screenshot provided).  Does anyone know what I could do?  Thanks!

P.S.  I'm not a beginner, but basic steps would be much appreciated :)  I have Ubuntu 12.04.

---

### Post by Cheesemill on 2012-04-29
You have an error in one of your apt sources.
I think I know what it is but to make sure can you enter the following in a terminal and paste the results please.
```
cat /etc/apt/sources.list.d/ojno-unity-minimize-on-click-precise.list
```

---

### Post by lektor on 2012-04-30
I have the same bug
> 
root@lektor-Aspire-4810T:/home/lektor# cat /etc/apt/sources.list.d/ojno-unity-minimize-on-click-precise.list
deb [http://ppa.launchpad.net/ojno/unity-minimize-on-click/ubuntu](http://ppa.launchpad.net/ojno/unity-minimize-on-click/ubuntu) precise main
deb-src [http://ppa.launchpad.net/ojno/unity-minimize-on-click/ubuntu](http://ppa.launchpad.net/ojno/unity-minimize-on-click/ubuntu) precise main
ain
root@lektor-Aspire-4810T:/home/lektor# 

give me an advice how fix this

---

### Post by Cheesemill on 2012-04-30
> **lektor said:**
> I have the same bug

give me an advice how fix this
Delete the third line of the file and you should be fixed.

---

### Post by lektor on 2012-04-30
thanks
```
sudo gedit /etc/apt/sources.list.d/ojno-unity-minimize-on-click-precise.list
```

---

### Post by Cheesemill on 2012-04-30
> **lektor said:**
> thanks
```
sudo gedit /etc/apt/sources.list.d/ojno-unity-minimize-on-click-precise.list
```

You should never use sudo with graphical applications. Always use gksudo instead.
But glad you got it fixed :)

---

