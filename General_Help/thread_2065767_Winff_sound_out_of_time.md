---
title: "Winff sound out of time ?"
date: 2012-10-02
forum: General Help
---

### Post by cowboy7305 on 2012-10-02
I have a MKV file and it plays well on my computer 
but i have to change it to AVI to play it on TV i have always used Winff with good results, but after i reinstalled 12.04 it is now got sound out of time with pic frames and it is also very minute stop starts through out the converted file
any one help 
many thanks

---

### Post by thatguruguy on 2012-10-02
You can try this, it sometimes helps synchronization issues. In the "FFmpeg" tab, add the following:
```
-async 1
```

---

