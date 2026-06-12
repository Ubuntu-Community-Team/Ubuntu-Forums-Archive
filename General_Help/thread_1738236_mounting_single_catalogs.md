---
title: "mounting single catalogs"
date: 2011-04-24
forum: General Help
---

### Post by chrisck on 2011-04-24
Hi, is that possible to mount single catalog? 
I want to move some folders from /home to another partition. I know how to move whole /home - edit /etc/fstab and add up one line in my case:
```
UUID=F0BA64BCBA648148 /home/chris auto defaults,noatime 0 0
```But I don't want to move everything, just few folders - Music, Video, Documents, because that's the files I want to share with windows. so I want to mount:
- sda4/Music into /home/chris/Music 
- sda4/Video into /home/chrisVideo
- sda4/Documents into /home/chris/documents

I assume that is possible, because in Linux world there is no impossible things, but how to do that?

---

