---
title: "amazon mp3 downloader - dependency not satisfiable"
date: 2012-01-31
forum: General Help
---

### Post by over_my_head on 2012-01-31
i tried to install amazon's mp3 downloader - i was able to download their file but when i open it the ubuntu software center window pops up and says 
> 
Dependency is not satisfiable: libboost-filesystem1.34.1


i looked in package manager but i don't have a libboost-filesystem1.34.1
i have some other libboost-filesystem versions but not that one. 

i can still download MP3 files from amazon but they end up in my downloads folder instead of in my music folder so this is really just an inconvenience but it would be nice to get it fixed.
thanks!
:-)

edited to add: i'm running ubuntu 11.1 as my operating system.

---

### Post by ruffEdgz on 2012-01-31
When you said 'install amazon's mp3 downloader', did you mean this link: [http://www.amazon.com/gp/dmusic/help/amd.html](http://www.amazon.com/gp/dmusic/help/amd.html)

If you are, it seems that Amazon hasn't updated those packages in some time now (Ubuntu 9.10 was release back in October 2009). I'm going to say that Amazon has given up on this project but I haven't searched for anything that says so.

Hope this helps.

---

### Post by oldos2er on 2012-01-31
There are a couple alternatives to Amazon's outdated mp3 downloader for Linux; [http://code.google.com/p/pymazon/](http://code.google.com/p/pymazon/) and [http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

---

### Post by CatKiller on 2012-02-01
You can get old packages as .deb files from packages.ubuntu.com.

The Amazon downloader is 32-bit only, so you'll need to use something like getlibs to get them installed if you're using 64-bit.

---

### Post by Brejcha on 2012-02-01
> **oldos2er said:**
> There are a couple alternatives to Amazon's outdated mp3 downloader for Linux; [http://code.google.com/p/pymazon/](http://code.google.com/p/pymazon/) and [http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

Pymazon is amazing! Great work!!!!!!!!! 

Just need to fix some issues with certain songs not being able to download because of foreign characters.

---

### Post by over_my_head on 2012-02-02
> 
When you said 'install amazon's mp3 downloader', did you mean this link: [http://www.amazon.com/gp/dmusic/help/amd.html](http://www.amazon.com/gp/dmusic/help/amd.html)


yep, that's the one. i was hoping that it would work with 11.10 despite having been written for 9.04 but no such luck.

thanks for the tips, i will check out the pymazon downloader.
:-)

---

### Post by MegaCreaton on 2012-02-16
If you have banshee all you need to do is get the  .amz file instructions here: [http://code.google.com/p/pymazon/wiki/HowToAmzDownload]("http://code.google.com/p/pymazon/wiki/HowToAmzDownload") then in banshee right-click on Music >Import  Media and then choose Amazon MP3 Purchase  and select he .amz file that you downloaded.

---

