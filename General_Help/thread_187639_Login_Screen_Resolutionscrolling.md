---
title: "Login Screen Resolution/scrolling"
date: 2006-06-03
forum: General Help
---

### Post by GazzaK on 2006-06-03
I've got a screen resolution problem on the login screen only as per [http://img61.imageshack.us/img61/3411/img00019kv.jpg](http://img61.imageshack.us/img61/3411/img00019kv.jpg) and [http://img61.imageshack.us/img61/313/img00025td.jpg](http://img61.imageshack.us/img61/313/img00025td.jpg) - when I move the mouse the screen scrolls about, once I have logged in, it is fine, any ideas?

---

### Post by GazzaK on 2006-06-03
I edited my xorg.conf as below
```
Section "Screen"
  Identifier "Default Screen"
  Device "NVIDIA Corporation NV40? [Unknown nVidia Card]"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1600x1200@85" "1024x768@75"
  EndSubSection
EndSection
```

ie took away loads of modes, and it now works great at a resolution of 1600x1200@85 :)

---

