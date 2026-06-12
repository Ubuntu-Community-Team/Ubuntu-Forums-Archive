---
title: "ocelot ppa problem"
date: 2012-01-29
forum: General Help
---

### Post by qwertyjjj on 2012-01-29
I get this when tryig to update:
```

Hit http://gb.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com oneiric-backports/universe Translation-en
Ign http://extras.ubuntu.com oneiric/main Translation-en
W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
j-media-centre@jmediacentre-A880G:~$ 


```

ALso, when following the tutorial to install xbmc: [http://www.noobslab.com/2011/09/install-xbmc-on-ubuntu-1110-oneiric.html](http://www.noobslab.com/2011/09/install-xbmc-on-ubuntu-1110-oneiric.html)
I get a screen asking me to click Ok for some fonts, except it is in some kind of DOS/terminal window and I cannot click Ok, pressing return does nothing.

tried removing them in the software sources and got:

```

Ign http://extras.ubuntu.com oneiric/main Translation-en_GB
Ign http://extras.ubuntu.com oneiric/main Translation-en
Fetched 7,096 B in 3s (2,009 B/s)
W: GPG error: http://packages.medibuntu.org oneiric InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
j-media-centre@jmediacentre-A880G:~$ 


```

---

### Post by Frogs Hair on 2012-01-29
The last build for the team/xbmc/ppa/ubuntu  is for 10.10  .  [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/) Did you run sudo apt-get update after removing the sources ?

---

### Post by kazztan0325 on 2012-01-29
Hi qwertyjjj,

You have to install **'medibuntu-keyring'** with Synaptic Package Manager or Software Center to solve GPG error.

And I found a thread of comments which have to do with the same problem in XBMC Community Forum:
[http://forum.xbmc.org/showthread.php?t=114486]("http://forum.xbmc.org/showthread.php?t=114486")

Hope this helps.

---

