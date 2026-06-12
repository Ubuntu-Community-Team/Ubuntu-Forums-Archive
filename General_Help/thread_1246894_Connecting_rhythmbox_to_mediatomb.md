---
title: "Connecting rhythmbox to mediatomb"
date: 2009-08-22
forum: General Help
---

### Post by nickeh on 2009-08-22
Recently installed mediatomb to my server. 

When i saw rhytmbox was able to use it I installed that to. But, how do i get rythmbox to connect to media tomb? I have enabled UPnP plugin but i can't find how to actually connect. And it doesn't happens automatically if that's what it's supposed to do. 

Any idea's on how to get this to work?

---

### Post by AndyCee on 2009-09-06
Try installing the "python-coherence" package.

```
sudo apt-get install python-coherence
```

---

### Post by nickeh on 2009-09-06
Yes have that without it the plugin didn't even load. Now the problem is that i check the plugin without any error. But nothing happened after that, no server list in the left list...

---

### Post by ursinha on 2010-07-04
I know it's been toooooo long since you posted this, but I faced the same problem today and decided to share the solution I found. You asked for Xubuntu, but since I'm using Ubuntu Lucid I guess the solution is pretty much the same. 

I have a Mediatomb server in my LAN, and to be able to see it from Rhythmbox, I had to install a package called rhythmbox-plugin-coherence:

```
sudo apt-get install rhythmbox-plugin-coherence
```

Now, you have to enable that in Rhythmbox: go in Edit, Plugins and enable "DLNA/uPnP sharing and control support". Automatically you should see the mediatomb share in the left bar.

Hope this helps!

---

