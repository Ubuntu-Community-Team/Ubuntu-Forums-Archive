---
title: "Repos"
date: 2009-11-16
forum: General Help
---

### Post by qwertyuiop96 on 2009-11-16
I've just gotten 9.10 after having 8.04 for forever.  9.10 is awesome, but stuff I'm used to isn't in the repos anymore.  For instance, the sun-java6 package and its Firefox plugin.  Also net-beans IDE, and I'm sure other stuff I haven't gotten yet.  How do I get back the old repos that had all the stuff?

---

### Post by audiomick on 2009-11-16
in the package manager: have you got universe and partner enabled?
possibly also you need to go to medibuntu again, and reinstall that as repo. That gets cancelled with every update.

---

### Post by hwttdz on 2009-11-16
It's very unlikely anything you need is not in the current repos.  sun-java6-plugin, will install most if not all the java goodies you need. If you don't see it it's possible you need to enable the universe repository in synaptic.  

sudo synaptic, then in settings repositories check the boxes you need, then you should be able to "apt-get update" "sudo apt-get install sun-java6-plugin".  Also while you're at it you might want to select the best server, so you get faster updates and the servers aren't hammered by the load.

---

### Post by drs305 on 2009-11-16
Do you have the multiverse and universe repositories enabled?  sun-java and the sun-java-plugin for mozilla are in the mulitverse repository (Synaptic or Software Sources, Settings, Repositories, Ubuntu Software).

---

### Post by audiomick on 2009-11-16
great minds think alike?:P

---

### Post by qwertyuiop96 on 2009-11-16
Multiverse and Universe are checked   OH - and I should say.  I do get some errors when the package info loads:

```

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/Release](http://archive.canonical.com/ubuntu/dists/karmic/Release)  Unable to find expected entry  universe/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

```

---

