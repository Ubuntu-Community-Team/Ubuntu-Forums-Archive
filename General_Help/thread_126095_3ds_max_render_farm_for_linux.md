---
title: "3ds max render farm for linux?"
date: 2006-02-05
forum: General Help
---

### Post by rjcoolpix880 on 2006-02-05
does ony one know of any render farm programs for 3ds-max that run in linux. i ask because i found 4 *old* comps and i figured if xp wasnt sucking up all the resources then maybe they could actually not be trash.

---

### Post by el3ktro on 2006-02-05
I used to work with 3ds max on Windows, too, but I've never heart of any such software. I always used the built-in network renderer back in my Windows times. Perhaps Google may be able to help your more ...

Tom

---

### Post by Ocxic on 2006-02-05
are you saying that 3dsmax runs on linux??? or are you using wine?

---

### Post by John.Michael.Kane on 2006-02-05
Looks like you would have to wine 3dsmax. from the os specs needed [http://usa.autodesk.com/adsk/servlet/index?siteID=123112&id=5659453](http://usa.autodesk.com/adsk/servlet/index?siteID=123112&id=5659453)

---

### Post by rjcoolpix880 on 2006-02-05
[QUOTE=Ocxic]are you saying that 3dsmax runs on linux??? or are you using wine?[/QUOTE]
no i am saying delete windows and run a purely linux box.
seems like using wine defeats the point.

---

### Post by gaspar on 2007-01-16
So, wine can really run 3ds max? 
Must try this, since it´s the only thing that stucks me with a windoze partition...

---

### Post by mfroble on 2007-12-04
I too  am interseted in setting up the same network. possibly using a windows 2003 server as a domain controller, linux on the nodes, however I am not sure what programs are easily availible as a queue manager

---

### Post by TrioTorus on 2007-12-06
There is DrQueue: [http://drqueue.org/cwebsite/](http://drqueue.org/cwebsite/)
There is even a version in the repos, but didn't manage to get it working last time I tried.

I now installed: Sun Grid Engine. It's a bit spartacan, but well documented, pretty easy to set up and rock solid. 

more info here: [http://www.sun.com/software/gridware/](http://www.sun.com/software/gridware/)
I even have an svg icon and .desktop file if you're interested.

---

