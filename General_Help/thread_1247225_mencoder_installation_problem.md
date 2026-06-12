---
title: "mencoder installation problem"
date: 2009-08-22
forum: General Help
---

### Post by OisinT on 2009-08-22
Trying to install devede, but I need mencoder first... so went to synaptic and tried to install it.

mencoder:
 Depends: libopencore-amrnb0 (>=0.1.1) but it is not installable
 Depends: libopencore-amrwb0 (>=0.1.1) but it is not installable

looked for both of them in synaptic but nothing... couple google searches and nothing also.  Any help appreciated.

---

### Post by michy99 on 2009-08-22
How are you trying to install devede? If you install it from the repositories, it should take care of all dependencies including mencode.

---

### Post by OisinT on 2009-08-22
yeah through synaptic.

> devede:
 Depends: mencoder but it is not going to be installed

So I then try to install mencoder by itself and no luck cuz of the 2 listed above.  Aggrivating.

---

### Post by michy99 on 2009-08-22
Post your sources.list file.```
cat /etc/apt/sources.list
```

---

### Post by OisinT on 2009-08-22
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ppa.launchpad.net/rvm/testing/ubuntu](http://ppa.launchpad.net/rvm/testing/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/rvm/testing/ubuntu](http://ppa.launchpad.net/rvm/testing/ubuntu) jaunty main
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main
deb [http://ppa.launchpad.net/rvm/mplayer/ubuntu](http://ppa.launchpad.net/rvm/mplayer/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/rvm/mplayer/ubuntu](http://ppa.launchpad.net/rvm/mplayer/ubuntu) jaunty main
deb [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/rvm/smplayer/ubuntu](http://ppa.launchpad.net/rvm/smplayer/ubuntu) jaunty main
deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) gutsy main universe
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) jaunty main

---

### Post by michy99 on 2009-08-22
Go to System -> Administration -> Software Sources and make sure that Multiverse and Restricted repositories are enabled.

---

### Post by michy99 on 2009-08-22
Also, you might want to change the gilir repository from gutsy to jaunty.

---

### Post by OisinT on 2009-08-22
> **michy99 said:**
> Go to System -> Administration -> Software Sources and make sure that Multiverse and Restricted repositories are enabled.
yep they're enabled. just double checked.

> **michy99 said:**
> Also, you might want to change the gilir repository from gutsy to jaunty.
did that and still no luck

---

### Post by michy99 on 2009-08-22
Run this in a terminal and post the output here:```
sudo apt-get install devede
```

---

### Post by OisinT on 2009-08-22
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  devede: Depends: mencoder but it is not going to be installed
E: Broken packages

```

---

### Post by michy99 on 2009-08-22
I think you may need the medibuntu repository.```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```Then```

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```Then try updating again.

---

### Post by mc4man on 2009-08-22
This is not a good idea to have as a source. While you could get away with have the 'sid' debian-multimedia as a source for a while, sooner than later it's going to cause you problems

deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main

I'd remove it as a source and then do a sudo apt-get update.

( if you needed the opencore amr libs then they are available here, should only be done as a **direct download** and  install

[http://debian-multimedia.org/dists/unstable/main/binary-i386/](http://debian-multimedia.org/dists/unstable/main/binary-i386/)
or
[http://debian-multimedia.org/dists/unstable/main/binary-amd64/](http://debian-multimedia.org/dists/unstable/main/binary-amd64/)

What, if any, depend issues you've created by having d-m etch as a source remains to be seen, either now or down the road

---

### Post by OisinT on 2009-08-22
> **mc4man said:**
> This is not a good idea to have as a source. While you could get away with have the 'sid' debian-multimedia as a source for a while, sooner than later it's going to cause you problems

deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main

I'd remove it as a source and then do a sudo apt-get update.

( if you needed the opencore amr libs then they are available here, should only be done as a **direct download** and  install

[http://debian-multimedia.org/dists/unstable/main/binary-i386/](http://debian-multimedia.org/dists/unstable/main/binary-i386/)
or
[http://debian-multimedia.org/dists/unstable/main/binary-amd64/](http://debian-multimedia.org/dists/unstable/main/binary-amd64/)

What, if any, depend issues you've created by having d-m etch as a source remains to be seen, either now or down the road
legend.

Thanks. removed it from the repos, directly downloaded the 2 I needed from there and problem is solved!
Thanks a lot!  Thanks to michy99 for your help too

---

