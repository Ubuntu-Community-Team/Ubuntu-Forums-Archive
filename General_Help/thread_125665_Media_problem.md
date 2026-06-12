---
title: "Media problem"
date: 2006-02-04
forum: General Help
---

### Post by malic on 2006-02-04
I also can not run any media file such as mp3 avi and mpg. If i attempt to run these files, system says* " There were no decoders found to handle the stream, you might need to install the corresponding plugins"* How can i install related plugins?

---

### Post by Qrk on 2006-02-04
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by malic on 2006-02-04
I typed related command **{sudo apt-get install  gstreamer0.8-mad}** in terminal then terminal reacted as below

> ismail@ubuntu:~$ sudo apt-get install  gstreamer0.8-mad
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/tr.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/tr.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/tr.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/tr.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/tr.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/tr.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/tr.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/tr.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/tr.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package gstreamer0.8-mad
ismail@ubuntu:~$


---

### Post by madmetal on 2006-02-04
try automatix to download all codecs needed its really easy and works great.

---

### Post by lamego on 2006-02-04
Just like it tells you on the last command you need to:
```
sudo apt-get update
```

---

