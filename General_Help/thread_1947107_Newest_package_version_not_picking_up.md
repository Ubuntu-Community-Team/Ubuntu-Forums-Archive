---
title: "Newest package version not picking up?"
date: 2012-03-26
forum: General Help
---

### Post by trbabb on 2012-03-26
Hi folks, I've got a question about how apt-get deals with package versions:

I'm experiencing this issue (related to the package libdca-utils):
  [http://bugs.debian.org/cgi-bi/bugreport.cgi?bug=639593](http://bugs.debian.org/cgi-bi/bugreport.cgi?bug=639593)

By the looks of that bug report, the issue has been fixed in the debian package (which Ubuntu would use, right?). However, when I run 'sudo apt-get update; sudo apt-get install libdca-utils', nothing appears to have changed (and I still get the bug). It kind of seems like I'm not picking up the fix mentioned in that bugreport.

What do I have to do to pick up the change? Why doesn't apt-get install give me the latest version?

I'm using Ubuntu Server 10.04 LTS.

Thanks!
-tb

---

### Post by dcstar on 2012-03-26
> **trbabb said:**
> 
.........
What do I have to do to pick up the change? Why doesn't apt-get install give me the latest version?
.........

Because Ubuntu releases never change the package versions that were originally packaged. You only get Security updates for those existing versions.

You might get later versions of some packages if you enable the Backports and Proposed repositories, but you will never get new versions of all packages because all the testing necessary to ensure compatibility is just too much.

If you want the new package then manually install the .deb file and hope that any dependency issues can be resolved.

---

### Post by trbabb on 2012-03-26
OK. So I take it this means that if and when I upgrade to Precise, I'll get the change?

---

### Post by 3rdalbum on 2012-03-26
> **trbabb said:**
> OK. So I take it this means that if and when I upgrade to Precise, I'll get the change?

Yes, if the change is in Precise you will get it automatically when you upgrade.

---

### Post by Frogs Hair on 2012-03-26
The package,  libdca-utils is part of another package and has been upgraded on 12.04 . [https://launchpad.net/ubuntu/+source/libdca](https://launchpad.net/ubuntu/+source/libdca)

---

