---
title: "Chromium Cache"
date: 2011-07-23
forum: General Help
---

### Post by WG- on 2011-07-23
Hello 

I have a question... Where does chromium puts its cache for flash video's? I watched a flash video and it got deleted just now. But I wanted to save it on my harddisk. I still can play the video so it must be in the cache somewhere... but I don't now where chromium caches flash video's...

So does anyone know where chromium caches flash video's?

---

### Post by TeoBigusGeekus on 2011-07-23
Post us the output of
```
lsof | grep Flash
```

---

### Post by WG- on 2011-07-23
> **TeoBigusGeekus said:**
> Post us the output of
```
lsof | grep Flash
```

Does not seem to give any output.

---

### Post by TeoBigusGeekus on 2011-07-23
Open the page with the video and let it load completely. Don't close the page and run the command again. Post us its output.

---

### Post by WG- on 2011-07-23
If I load it again the video will be gone because it got deleted, but I will try with another video.

---

### Post by TeoBigusGeekus on 2011-07-23
Deleted.

---

### Post by WG- on 2011-07-23
chromium- 32423     <name>   25u      REG        8,5   1029950   4063622 /tmp/FlashXXMnrFOe (deleted)
chromium- 32423     <name>   27u      REG        8,5  39779864   4063824 /tmp/FlashXXkkloj9 (deleted)
chromium- 32423     <name>   44u      REG        8,5  25429655   4063621 /tmp/FlashXX5GaFZN (deleted)

Oh and I went to the tmp folder but the folders are not there (deleted).

---

### Post by TeoBigusGeekus on 2011-07-23
```
cp /proc/32423/fd/25 ~/Desktop/vid1.flv
cp /proc/32423/fd/27 ~/Desktop/vid2.flv
cp /proc/32423/fd/44 ~/Desktop/vid3.flv
```

The videos are on your desktop now.

---

