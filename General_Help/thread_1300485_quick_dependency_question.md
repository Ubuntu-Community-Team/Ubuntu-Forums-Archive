---
title: "quick dependency question"
date: 2009-10-25
forum: General Help
---

### Post by pavel989 on 2009-10-25
just did an upgrade to jaunty, and got my ati hd 2600 working (WOO), and got my realtime kernel working.

im trying to install emc2, and get this:

  Depends: python (<2.6) but 2.6.2-0ubuntu1 is to be installed
 Recommends: emc2-firmware but it is not going to be installed

I dunno what repo i should enable. or maybe theres a work around?

---

### Post by rockstarrem on 2009-10-25
```

sudo apt-get install python2.6-dev

```

Is that installed?

---

### Post by pavel989 on 2009-10-25
yup it is

---

