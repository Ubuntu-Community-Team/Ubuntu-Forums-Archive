---
title: "Not enough space on my filesystem..."
date: 2009-12-07
forum: General Help
---

### Post by bittiez on 2009-12-07
Hey guys, I am fairly new to ubuntu, and I love it so far. I am dual booting with Windows 7 and ubuntu, windows 7 has a 120gb harddrive partition, and I just did 4gb for my ubuntu thinking I could install apps and such on my other partition, but I'm not sure how to do this, or if its possible at all?

---

### Post by cariboo on 2009-12-07
You can't install Ubuntu programs on a Windows partition, as when a program is installed various parts of the program go in /usr/bin, /usr/lib and /usr/share. If you are running out of space, Open an Applications-->Accessories-->Terminal and type:

```
sudo apt-get clean
```

The above command will removed archived packages from /var/cache/apt/archives. Then type:

```
sudo apt-get autoremove
```

The above command will remove unneeded dependencies.

---

### Post by Cheesemill on 2009-12-07
I'd recommend giving Ubuntu at least 10GB if you want to install more apps.

---

### Post by bittiez on 2009-12-07
Alright thank you very much.

---

