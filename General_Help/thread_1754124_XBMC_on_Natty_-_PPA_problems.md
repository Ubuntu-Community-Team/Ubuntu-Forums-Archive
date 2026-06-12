---
title: "XBMC on Natty - PPA problems"
date: 2011-05-09
forum: General Help
---

### Post by wittzi on 2011-05-09
I'm trying to install XBMC on my 11.04 Ubunto laptop.  I've added the ppa:team-xbmc repository, but when I update I get the following error messages:
[B]
W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found[/B]

This is understandable, as there are no natty directories as the latest is maverick (complete list [here]("http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/")).  However, is there a way that I can have a blast at installing it from the Maverick repository instead or has anyone found a way of getting it working?

It would be good to be able to stream to the laptop, but at the moment I'm struggling to get it installed.  Any advice would be greatly appreciated!

---

### Post by Aenima99x on 2011-05-09
You can use the XBMC unstable repo to get it installed.
```
http://ppa.launchpad.net/team-xbmc/unstable/ubuntu
```

---

### Post by lakerssuperman on 2011-05-09
I am running the XBMC from this repo and it is fairly stable.  I am also using the yaVDR unstable repo on another machine because it provides VAAPI support which is a plus if you have an ATI based video setup and can't utilize VDPAU.

---

### Post by tctx on 2011-05-20
Yes, you can use xbmc's maverick repository on natty.

```
sudo gedit /etc/apt/sources.list.d/team-xbmc-ppa-natty.list
```

Replace "natty" with "maverick".

```
sudo apt-get update
sudo apt-get install xbmc
```

I haven't encountered any problems using this setup.

---

### Post by Machiavelli on 2011-09-07
> **tctx said:**
> Yes, you can use xbmc's maverick repository on natty.


Thanks bro, that did the trick for me as well. :D

---

### Post by wittzi on 2011-11-09
Thanks to everyone - all working perfectly now.  However, now I'm interested in OpenELEC as it's all from USB and is super-fast!!

---

