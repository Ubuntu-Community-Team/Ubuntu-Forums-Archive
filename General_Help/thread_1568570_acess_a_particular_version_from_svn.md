---
title: "acess a particular version from svn"
date: 2010-09-05
forum: General Help
---

### Post by nandan.amar on 2010-09-05
how can I get/receive a particular revision of a package from svn..??
say revision XX from url svn://svn.ffmpeg.org/ffmpeg/trunk.
is following ok??
svn checkout -r XX svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg

---

### Post by FakeOutdoorsman on 2010-09-06
You will also need to checkout an appropriate *libswscale* revision. See [this post](http://ubuntuforums.org/showpost.php?p=9810674&postcount=1247) for an example

---

