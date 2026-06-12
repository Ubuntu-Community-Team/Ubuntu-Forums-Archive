---
title: "DVDs"
date: 2009-09-17
forum: General Help
---

### Post by HalfCrackedTech on 2009-09-17
what is the process to get DVDs to run in Ubuntu?

---

### Post by briantoumbs on 2009-09-17
You need to install the codecs for them.
```
sudo apt-get install ubuntu-restricted-extras

```

---

### Post by x C0MMAND0 x on 2009-09-17
First, run the following command:

```
sudo apt-get install libdvdread4
```

Second, run the following command:

```
/usr/share/doc/libdvdread4/install-css.sh
```

Third, I would download a player that works very well like VLC.

```
sudo apt-get install vlc
```

Let me know how that works for you.

---

### Post by jmszr on 2009-09-17
HalfCrackedTech,

You also should install Medibuntu: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) .

Then, make sure you install:```
sudo apt-get install libdvdcss2
```

+1 VLC

---

### Post by HalfCrackedTech on 2009-09-17
That all worked.

Thank you all!

---

