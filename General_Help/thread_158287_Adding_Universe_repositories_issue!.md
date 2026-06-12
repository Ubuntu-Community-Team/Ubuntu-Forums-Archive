---
title: "Adding Universe repositories issue!"
date: 2006-04-10
forum: General Help
---

### Post by Dantrag on 2006-04-10
Well gratz to me...I am posting from my newly installed Ubuntu box. Took me forever to get it up and running and on the internet (dang conextant dial up modem). 99% of it was user error though but I learned alot and stuck with it and I have been successful. On my way to being window$ free! :D 
Now on to my problem. I am unable to add the universe repository in either apt-get or synaptic. I get the following error message:
[SIZE="3"][FONT="Arial"]Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)[/FONT][/SIZE]
So what have I done wrong. Any help would be appreciated. Thanks!
Dantrag
linux n00b

---

### Post by aysiu on 2006-04-10
Try the bottom of this page:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by paulipe on 2006-04-10
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo vi /etc/apt/sources.list
```

Now uncomment the following lines
```
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://security.ubuntu.com/ubuntu breezy multiverse
deb-src http://security.ubuntu.com/ubuntu breezy multiverse

deb http://ubuntu-backports.mirrormax.net/ breezy-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main universe multiverse restricted

```

If the lines don't exist then type it out. Then do a

```
sudo apt-get update
```

Hope it helps and the problem was not something specific to your net connection being able to connect to these sites and not those.

---

### Post by Sef on 2006-04-10
Here's from the wiki:

[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

Snapshots are included here.

---

