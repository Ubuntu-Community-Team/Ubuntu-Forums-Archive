---
title: "Upgrade weirdness"
date: 2010-05-23
forum: General Help
---

### Post by veggen on 2010-05-23
I wanted to upgrade my Karmic to Lucid today but gave up after seeing some very weird changes in the list. So, if someone can shed some light on any of the following, it would be great:

1 - Size: How come I need to download 1.3 GB for the upgrade when whole Lucid is 700MB big?

2 - Gnometris: Why would the upgrade remove Gnometris, what does it have to do with anything?

3 - IcedTea: Why would the upgrade install IcedTea even though I already have Sun JDK/JRE installed? Shouldn't it leave Java to me? Also, since I apparently have to let it install IcedTea, will it cause some collision with the existing Java plugin? How can I choose what to use?

If you know something about any of these, please share the info :)

---

### Post by skarme on 2010-05-23
Might as well make a live CD and then upgrade using it.

---

### Post by veggen on 2010-05-23
I guess that could help about the first issue...

---

### Post by happyhamster on 2010-05-23
> **veggen said:**
> I wanted to upgrade my Karmic to Lucid today but gave up after seeing some very weird changes in the list. So, if someone can shed some light on any of the following, it would be great:

1 - Size: How come I need to download 1.3 GB for the upgrade when whole Lucid is 700MB big?
The cd contains a default core install, but the upgrade will also cover anything else you chose to install for Karmic.

> 
2 - Gnometris: Why would the upgrade remove Gnometris, what does it have to do with anything?
It will return as "Quadrapassel". A rename, and it uses another graphical engine IIRCC.
[http://live.gnome.org/Gnometris](http://live.gnome.org/Gnometris)

> 
3 - IcedTea: Why would the upgrade install IcedTea even though I already have Sun JDK/JRE installed? Shouldn't it leave Java to me? Also, since I apparently have to let it install IcedTea, will it cause some collision with the existing Java plugin? How can I choose what to use?

Don't know about java, there's this though:
[http://www.ubuntu.com/getubuntu/releasenotes/1004#Sun](http://www.ubuntu.com/getubuntu/releasenotes/1004#Sun) Java moved to the Partner repository

Good luck.

---

### Post by veggen on 2010-05-23
Great tips, thanks a bunch!
Regarding Java, it seems I get OpenJDK and IcedTea installed because I had the Ubuntu restricted package installed and it's now changed to includede the two mentioned libraries. I'll hopefully manage to resolve any resulting conflicts.

---

