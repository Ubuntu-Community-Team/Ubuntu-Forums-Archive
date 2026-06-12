---
title: "Slow downloads on package manager"
date: 2009-09-01
forum: General Help
---

### Post by Big Gaz on 2009-09-01
I'm vary new to Ubuntu and have a question about package manager speed and install packages.

Until yesterday I was having no problems downloading and installing packages, but now i select a package (k3b) and select apply etc...

The files start to download and a few percentage is indicated, then it slows down to a download rates of unknown and even small files of a few 100kb take 10's of minutes to download?

Is this normal?

the rest of the box works ok, web browsing etc, so I don't have a internet issue outside of package manager

Ubuntu 9.04 and Synaptic

Thx

Garry

---

### Post by drs305 on 2009-09-01
You can try a different server. Open Synaptic or Software Sources (System, Administration). Go to Settings, Repositories. In the Ubuntu Software tab, go to "Download from", click on the box and select "Other". Then press "Choose Best Server". A test will run and the recommended server will be highlighted.

Note the "Best Server" will change based on conditions so you should reaccomplish this test from time to time, especially if the server is far away or you notice the download speeds again slow down.

---

### Post by Big Gaz on 2009-09-01
just tried what you have asked as there appears to be a problem here also?

the available servers where all pinged very quickly up towards the last few, then the process stalled for a few seconds, before finishing.

I selected the best server and it asked me to reload the package info.

It shot off and did the first 27 and stalled again, this time at universal packages , it got to 85% and now is frozen there and showing 233b/sec or unknown (very very slow)

It's as if the internet link is being strangled after a burst of activity?

going to try and do some downloads from internet to see if the problem is ISP

---

### Post by 3rdalbum on 2009-09-01
What you're describing sounds like you're using mobile broadband in a dead zone (I live in one). After a while when you're downloading any large files, it will slow to 230 bytes per second, then nothing, and the only thing you can do is hit Cancel and try again.

Mobile broadband works alright when you're in an area of good signal strength, but it's no substitute for wired internet.

---

### Post by Big Gaz on 2009-09-01
it looks like i'm having some random ISP issues.

ISP looking into it at the moment.

Just very strange how the speed is ok at the beginning and then drops out after time.

---

### Post by Big Gaz on 2009-09-01
i'm back online after some ISP issues and i'm still getting the same trouble with package manager....

when i do an update it flys for say 20 out of the 47 whatevers, then the speed drops to nothing, then after a few minutes it ramps up again and i get the next 10 at full speed then slows down again?

---

### Post by msinkm on 2009-09-09
I have been plagued with this problem for months, but I tried the "choose best server" approach today, and I got full speed downloads.  I'm convinced it is server load.

---

