---
title: "Can't seem to play DVDs."
date: 2010-03-13
forum: General Help
---

### Post by Everynameistaken on 2010-03-13
I have the restricted package installed and DVDs work on the same player in Windows, so it's not a hardware issue.

Movie Player stops responding and VLC player gives "can't read the file" errors over and over.

---

### Post by wojox on 2010-03-13
Try:

```
sudo apt-get install libdvdread4
```

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by Everynameistaken on 2010-03-13
Okay, it said libdvdread4 was already installed, but the second command did something and now it works.

I assumed it installed the package in the proper place (usr/share/doc/ and so forth)?  I see that sort of command a lot and I'm not totally sure what it does and when it's necessary.

---

### Post by wojox on 2010-03-14
Cool, could you mark the thread as solved for future searchers please.

---

