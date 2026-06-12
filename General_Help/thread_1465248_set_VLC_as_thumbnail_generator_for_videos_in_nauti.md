---
title: "set VLC as thumbnail generator for videos in nautilus"
date: 2010-04-29
forum: General Help
---

### Post by srg84 on 2010-04-29
Hi,

¿Is there a way to put VLC as default thumbnail generator for Videos in Nautilus?. I removed totem from system because i never use it..

---

### Post by srg84 on 2010-05-04
Maybe with a script...

**1 - Take the hash Md5 of video filename.**

for i in $( ls ); do m5sum $i > $i.md5;

**2 - Capture image thumbnail with VLC**

./vlc -V image --start-time 0 --stop-time 1 --image-out-format jpg --image-out-ratio 24 --image-out-prefix snap $i

**3 - Rename "snap" to md5 name.**

....

**4 - Copy thumbnail to home folder**

cp $md5name ~/thumbnails/normal



**Something like this should work please help.**

[http://ubuntuforums.org/showthread.php?t=666742&page=2](http://ubuntuforums.org/showthread.php?t=666742&page=2)

---

