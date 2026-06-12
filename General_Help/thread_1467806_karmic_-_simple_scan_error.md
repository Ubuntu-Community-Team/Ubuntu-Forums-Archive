---
title: "karmic - simple scan error"
date: 2010-05-01
forum: General Help
---

### Post by jasonmchristos on 2010-05-01
simple scan error as follows:  Failed to save file ImageMagick returned error code 11 Command line: convert -adjoin /tmp/simple-scan-DA9MBV.jpg /tmp/simple-scan-XCK4BV.jpg /tmp/simple-scan-NZVYBV.pdf Stdout: Stderr:  using karmic   note: I have apparmor extra profiles installed but didn't notice one that related to simple scan or imagemagick. Red herring or not?

---

### Post by DawieS on 2010-05-01
Are you using Xsane?

Xsane requires the destination folder to be private (not readable by others). Either use 'sudo nautilus' to set the permissions, or click on the 'create folder' tab (next to the stiffy save icon), in which case a destination folder with the correct permissions will be created.:smile::smile:

---

### Post by jasonmchristos on 2010-05-01
> **DawieS said:**
> Are you using Xsane?

Xsane requires the destination folder to be private (not readable by others). Either use 'sudo nautilus' to set the permissions, or click on the 'create folder' tab (next to the stiffy save icon), in which case a destination folder with the correct permissions will be created.:smile::smile:

 no this is simple scan not xsane and that couldnt be the problem as i tried to save it too desktop. however as u can tell it does the conversion in the tmp folder

---

### Post by Robert Ancell on 2010-05-02
Simple Scan bug is here:
[https://bugs.edge.launchpad.net/simple-scan/+bug/539381](https://bugs.edge.launchpad.net/simple-scan/+bug/539381)

There is a bug in the Karmic version of ImageMagick.  I haven't tried this, but S. Hisken reports that using the ImageMagick in this PPA solves the problem:
[https://launchpad.net/~raimar-sandner/+archive/ppa](https://launchpad.net/~raimar-sandner/+archive/ppa)

---

### Post by jasonmchristos on 2010-05-04
yes i am reporting the bug now dmesg returns convert[22234]: segfault at 3220 ip 00cc3f39 sp bfa570e0 error 6 in libMagickCore.so.2.0.0[be6000+1d2000]

---

### Post by jasonmchristos on 2010-05-04
bug reported here ... [https://bugs.launchpad.net/ubuntu/+source/imagemagick/+bug/574972](https://bugs.launchpad.net/ubuntu/+source/imagemagick/+bug/574972)[https://bugs.launchpad.net/ubuntu/+source/imagemagick/+bug/574972](https://bugs.launchpad.net/ubuntu/+source/imagemagick/+bug/574972)

---

### Post by jasonmchristos on 2010-05-04
> **Robert Ancell said:**
> Simple Scan bug is here:
[https://bugs.edge.launchpad.net/simple-scan/+bug/539381](https://bugs.edge.launchpad.net/simple-scan/+bug/539381)

There is a bug in the Karmic version of ImageMagick.  I haven't tried this, but S. Hisken reports that using the ImageMagick in this PPA solves the problem:
[https://launchpad.net/~raimar-sandner/+archive/ppa]("https://launchpad.net/%7Eraimar-sandner/+archive/ppa")

thank you Mr. Ancell it worked

sudo add-apt-repository ppa:raimar-sandner/ppa
sudo apt-get update
sudo apt-get upgrade

---

