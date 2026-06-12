---
title: "KMenu image problem"
date: 2006-05-16
forum: General Help
---

### Post by Melciah on 2006-05-16
Is it possible to remove the image with the cog on the left side of the Kmenu. For some reason it really bothers me. Thanks

---

### Post by MartinJ on 2006-05-16
Yes, the option is 'Show Side Image'.  It's buried quite deep in the System Settings though.

Try going to Panel -> Panels -> Menus

I can post a screenshot if you can't find it.

---

### Post by Melciah on 2006-05-17
thanks. i managed to find it alright

---

### Post by aysiu on 2006-05-17
These two commands take care of it: ```
sudo mogrify -resize 1x50 /usr/share/apps/kicker/pics/kubuntu-kmenu-side.png
killall kicker
```

---

