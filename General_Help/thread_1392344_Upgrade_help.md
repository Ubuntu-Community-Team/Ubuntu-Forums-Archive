---
title: "Upgrade help"
date: 2010-01-28
forum: General Help
---

### Post by Zypster on 2010-01-28
I'm still very green @ this linux stuff!!! I've done this upgrade from 8.10 to 9.04. I seem to remember a terminal (command line) method. Is there an easier way to upgrade from 9.04 desktop to 9.10 with the Livedisk or image on a flash drive??? I just wasted 4 hours trying the
Update Manager (method) & it crashed & burned after finishing on the file download. It said I lost 28 some-odd packages. I was able to do a partial upgrade.
Please help! 
Zypster

---

### Post by raktarok on 2010-01-28
Hi,

Try the alternate cd update method from here.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by Zypster on 2010-01-28
That was the first thing I tried, but the when I insert my cd It fails to load (auto start). When try the command that's posted there I get nothing either??? I'm totally lost here. Any suggestions would be great.
Thanks, Z

---

### Post by raktarok on 2010-01-28
Not sure if you tried this, but did you mount the iso you downloaded? There was no need to burn it to cd, actually. Assuming that your iso is in Desktop, issue this command from a terminal.

```
sudo mount -o loop ~/Desktop/ubuntu-9.10-alternate-i386.iso /media/cdrom0
```

Then if you don't get an autorun dialog, try this from the terminal:

```
gksu "sh /cdrom/cdromupgrade"
```

Post errors, if any. This should work though. and sorry if you have already tried these methods, maybe you have a bad copy of the iso?

---

