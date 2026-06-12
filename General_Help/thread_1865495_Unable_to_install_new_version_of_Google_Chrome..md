---
title: "Unable to install new version of Google Chrome."
date: 2011-10-20
forum: General Help
---

### Post by midion on 2011-10-20
I get an error also in the software center and i'm using ubuntu 11.10/

---

### Post by mc4man on 2011-10-20
> **midion said:**
> I get an error also in the software center and i'm using ubuntu 11.10/
There will be an update to software center that fixes this at some point.
If not wanting to wait install either  lzma **or** xz-lzma

---

### Post by howefield on 2011-10-20
Post spliced off to own thread.

You could also probably install via terminal.

```
sudo dpkg -i pathtofile
```

---

### Post by vasa1 on 2011-10-20
> **howefield said:**
> Post spliced off to own thread.

You could also probably install via terminal.

```
sudo dpkg -i pathtofile
```

This may not be clear to most newcomers.

---

### Post by mc4man on 2011-10-20
here's is the current bug (in progress/fix commited
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/868188](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/868188)

---

