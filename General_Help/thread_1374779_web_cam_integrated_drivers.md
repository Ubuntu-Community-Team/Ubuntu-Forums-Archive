---
title: "web cam integrated drivers"
date: 2010-01-07
forum: General Help
---

### Post by micio8 on 2010-01-07
Hi,

In order for ubuntu to detect my web cam on HP dv6000 i nedd to follow 2 steps>
a. You have to verify that you’ve installed svn           ...........DONE!
b. You have to remove some modules such as ry5u870 or r5u870 

how can i do step b?

---

### Post by 3rdalbum on 2010-01-07
> **micio8 said:**
> Hi,

In order for ubuntu to detect my web cam on HP dv6000 i nedd to follow 2 steps>
a. You have to verify that you&#8217;ve installed svn           ...........DONE!
b. You have to remove some modules such as ry5u870 or r5u870 

how can i do step b?

To temporarily remove these modules, you would do this:

```
sudo modprobe -r ry5u870
sudo modprobe -r r5u870
```

---

### Post by micio8 on 2010-01-07
Ive tried but i get

FATAL: Module r5u870 not found 
and
FATAL: Module ry5u870 not found

so when i type

[FONT=Arial][COLOR=Black]svn co [http://svn.mediati.org/svn/r5u870/trunk](http://svn.mediati.org/svn/r5u870/trunk) ~/r5u870
cd ~/r5u870
sudo make                                       AT THIS STEP I GET ERROR!
sudo make install
sudo modprobe r5u870[/COLOR][/FONT]

---

