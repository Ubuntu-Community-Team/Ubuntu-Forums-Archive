---
title: "MediaInfo .deb Trouble"
date: 2009-12-11
forum: General Help
---

### Post by prem1er on 2009-12-11
Is anyone else having trouble installing the deb packages from source forge for MediaInfo? I keep getting errors such as this...

> Error: Dependency is not satisfiable: libzen0 (>= 0.4.9)

I found this post and tried the .debs that mc4man posted and I'm still getting similar errors. Is anyone else having this problem?

[http://ubuntuforums.org/showthread.php?p=8314581](http://ubuntuforums.org/showthread.php?p=8314581)

---

### Post by mc4man on 2009-12-11
The mediainfo ppa has got it's builds squared away, use that for all 3 .debs ( or add the ppa to your sources.
The'official' site remains without a current libzen0
[https://launchpad.net/~shiki/+archive/mediainfo](https://launchpad.net/~shiki/+archive/mediainfo)

If you were to download and install the .deb's individually the proper order is 
libzen0
libmediainfo0
mediainfo (gui)

---

### Post by prem1er on 2009-12-11
Oh, thank you. I could not find these last night. I will try it when I get home. The official site really does need to get things cleaned up, things are linked all wrong and and it is just one big mess.

---

