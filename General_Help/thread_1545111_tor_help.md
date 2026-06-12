---
title: "tor help"
date: 2010-08-03
forum: General Help
---

### Post by zerobinary on 2010-08-03
I have made a mistake in regard to the file /etc/init.d/polipo.
I replaced the original code with the code on [https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf](https://svn.torproject.org/svn/torbrowser/trunk/build-scripts/config/polipo.conf)
Now I can't even reinstall the app, I have even tried to purge it.
Nevertheless, I could not remove the app.
I am just wondering does anyone have the file? So i can resolve the problem, please!

---

### Post by pricetech on 2010-08-03
I don't have the file or you'd be welcome to a copy of mine.

I'm guessing you didn't make a backup before you edited.

```
sudo cp /etc/init.d/polipo /etc/init.d/polipo.orig
```

---

