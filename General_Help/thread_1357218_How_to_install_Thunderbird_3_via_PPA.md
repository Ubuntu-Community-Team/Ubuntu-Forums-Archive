---
title: "How to install Thunderbird 3 via PPA"
date: 2009-12-17
forum: General Help
---

### Post by running_rabbit07 on 2009-12-17
I have seen many threads where people were having problems getting Thunderbird 3 installed, so here is how I did it. Add ```
http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu
``` to your sources list.```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247510BE
``````
sudo apt-get update
``````
sudo apt-get install thunderbird-3.0
```If anyone wants to add to this, please feel free.

---

### Post by Sin@Sin-Sacrifice on 2009-12-17
Hey thanks... very helpful.

---

### Post by picimaci on 2009-12-23
This post rocks :D

Anyway, one more thing:
Don't forget to install thunderbird-3.0-gnome-support

```

sudo apt-get install thunderbird-3.0-gnome-support

```

---

### Post by talktorishav on 2010-01-15
I found a detailed post here,
[http://techspalace.blogspot.com/2010/01/thunderbird-3-in-ubuntu.html](http://techspalace.blogspot.com/2010/01/thunderbird-3-in-ubuntu.html)

Recommended for newbie.

---

