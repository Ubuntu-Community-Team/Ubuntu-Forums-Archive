---
title: "Devede Dependencies"
date: 2009-09-28
forum: General Help
---

### Post by lakerssuperman on 2009-09-28
Hello,

I am trying to install Devede.  I am running 9.04.  I have all repositories enabled.  However, when I attempt to install Devede from Synaptic it tells me that Dvdauthor and Vcdimager cannot be found.  I have double checked and searched for them and sure enough they are not there.  Anyone have a similar situation with this.  Any help would be appreciated.

---

### Post by scouser73 on 2009-09-28
You can install DeVeDe from the GetDeb website: [[COLOR="Red"]**GetDeb - DeVeDe**[/COLOR]]("http://www.getdeb.net/search.php?keywords=devede")

---

### Post by lakerssuperman on 2009-09-28
I tried that as well.  When I install the Getdeb file from the terminal it gives me the following:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package devede_3.14.0-0~getdeb1_all.deb

I am unsure why since it reads the state information and then says it can't find the package.  I tried re downloading the file but it gives the same results.

---

### Post by oldos2er on 2009-09-28
Make sure you have the multiverse repository enabled. System, Administration, Software Sources.

---

### Post by lakerssuperman on 2009-09-28
I checked my sources.  First thing I did.  Unfortunately I missed that for some reason the universe repo wasn't enabled.  Haha.  Thank's for making me double check.

---

### Post by 3rdalbum on 2009-09-28
> **lakerssuperman said:**
> I tried that as well.  When I install the Getdeb file from the terminal it gives me the following:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package devede_3.14.0-0~getdeb1_all.deb

I am unsure why since it reads the state information and then says it can't find the package.  I tried re downloading the file but it gives the same results.

Incorrect:

```
sudo apt-get install devede_3.14.0-0~getdeb1_all.deb
```

Correct:

```
sudo dpkg -i devede_3.14.0-0~getdeb1_all.deb
```

Also correct and better: Double-click on the package and it launches the GDebi package installer.

Before Gdebi came along we had to use dpkg -i, and it doesn't resolve dependencies (it merely tells you what's missing)... thank goodness we've moved on from those times!

---

