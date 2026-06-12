---
title: "How do I get 'rar' package ?"
date: 2011-10-30
forum: General Help
---

### Post by ahmadka on 2011-10-30
Hi all .. I recently installed another Ubuntu after a long time and I'm trying to install 'rar' package on it as I use that for compression from within Terminal.

'rar' isn't found when I do

```
apt-get install rar
```

I have even tried doing

```
apt-get update
```

but even after then Ubuntu cannot find 'rar'. So how do I get it ?

---

### Post by Lars Noodén on 2011-10-30
Which version of Ubuntu are you using?  I found [rar](http://packages.ubuntu.com/oneiric/rar) to be available in Oneiric.

---

### Post by ahmadka on 2011-10-30
I'm using 10.04 32 bit ..

---

### Post by Lars Noodén on 2011-10-30
It looks like rar is available for 10.04: [http://packages.ubuntu.com/lucid/rar](http://packages.ubuntu.com/lucid/rar)

What is the exact error message you are getting from apt-get?

---

### Post by WasMeHere on 2011-10-30
Hello ahmadka,

Do you need the rar package specifically, or do you need to open (unrar) some rar files? If the latter, you can right-click on the rar file in the browser, and the archiver should be able to do the job.

Otherwise, I think you can find it on the internet for example [[COLOR="RoyalBlue"]_http://www.rarlab.com/download.htm_[/COLOR]]("http://www.rarlab.com/download.htm")

Have fun finding out :-)
Olle

---

### Post by ahmadka on 2011-10-30
This is the error I'm getting:

```
root@hosted-by:~# apt-get install rar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate
root@hosted-by:~#
```

---

### Post by Lars Noodén on 2011-10-30
What about this?

apt-get --fix-broken install rar

---

### Post by ahmadka on 2011-10-30
Well actually I just used wget to manually fetch the package from the mirrors pointed out by Lars ... then installed it .. problem solved .. Thanks Lars ! :)

---

### Post by Lars Noodén on 2011-10-30
Great, but in the longer term it would be good to fix what was wrong with APT.

---

