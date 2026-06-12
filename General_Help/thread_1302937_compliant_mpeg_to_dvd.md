---
title: "compliant mpeg to dvd"
date: 2009-10-27
forum: General Help
---

### Post by neoroses on 2009-10-27
so i used winff to make several DVD compliant mpegs, and i want to burn them/author them with out re-encoding them which devede/mandvd etc wants to do. so is there any way to just sort it so its a dvd iso or somthing similar?

---

### Post by neoroses on 2009-10-27
pleeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeease

---

### Post by nikosapi on 2009-10-27
If they are in fact, dvd-compatible then you should be able to make an ISO like so:
```
dvdauthor -o dvd -t some-video.mpg
dvdauthor -o dvd -T
mkisofs -dvd-video -o dvd.iso dvd
```

You'll need to have dvdauthor and mkisofs installed.

---

### Post by neoroses on 2009-10-28
thank you! sorted! magic!

---

