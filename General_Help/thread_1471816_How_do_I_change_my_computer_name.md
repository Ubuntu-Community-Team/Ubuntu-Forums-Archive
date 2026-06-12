---
title: "How do I change my computer name?"
date: 2010-05-03
forum: General Help
---

### Post by Ambidextrous on 2010-05-03
I was a bit hasty hitting "Okay" when I installed 10.4 and, as a result, I have a ridiculously long computer name.  How can I change it?

I have read a number of posts quite critical of this release.  I love it.  For the first time since I switched to Nvidia graphics cards I can get a graphical environment - straight out of the box.

TIA

---

### Post by fooey on 2010-05-03
sudo pico /etc/hostname

---

### Post by WorMzy on 2010-05-03
```
gksu gedit /etc/hostname
```

then

```
gksu gedit /etc/hosts
```

---

### Post by Iowan on 2010-05-03
> **WorMzy said:**
> ```
gksu gedit /etc/hostname
```

then

```
gksu gedit /etc/hosts
```If you don't change them both, **sudo** will complain...:D

---

### Post by Ambidextrous on 2010-05-04
Thank you all.

---

