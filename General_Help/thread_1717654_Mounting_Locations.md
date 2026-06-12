---
title: "Mounting Locations?"
date: 2011-03-30
forum: General Help
---

### Post by hotshot247 on 2011-03-30
is their any way to change the mounting location of your hard drives so when you click a certain hard drive in nautilus, it'll go to that location instead of the default one?

---

### Post by nothingspecial on 2011-03-30
I think you would have to use fstab or mount it yourself.

I don't know of any way to do it with nautilus.

That doesn't mean there isn't a way.

---

### Post by newbuntuxx on 2011-03-30
Yes. To do that, you'll need to edit your fstab file and make an entry. I assume you are referring to a backup partition/drive.


```
cd /etc
sudo nano fstab
```

At the bottom of the file, add:

```

/dev/sdax       /media/whatever      auto      rw,user  0 2


```

/dev/sdax: your device
/media/whatever: your mount point

---

