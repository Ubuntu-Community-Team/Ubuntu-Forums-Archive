---
title: "installing vlc"
date: 2006-03-23
forum: General Help
---

### Post by spako on 2006-03-23
hi, is there a way to install vlc with apt-get?

also how do i find out if certain applications are available via apt-get?

---

### Post by Qrk on 2006-03-23
It is already in the repositories. You can get it via synaptic (System-->Administration-->Synaptic Package Manager) or apt-get it (sudo apt-get install vlc) once you have enabled the extra repositories. To do that, type

```
sudo gedit /etc/apt/sources.list
```

and take out the # in the lines with the links in them.

---

### Post by spako on 2006-03-23
thanks for that, editing source.list was what i was missing!

---

