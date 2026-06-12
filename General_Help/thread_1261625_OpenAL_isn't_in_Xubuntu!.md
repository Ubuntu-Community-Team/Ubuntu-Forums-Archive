---
title: "OpenAL isn't in Xubuntu!?"
date: 2009-09-08
forum: General Help
---

### Post by CyanPrime on 2009-09-08
How do I install openAL for Xubuntu? I've tried add/remove, the package manager and apt-get, but nothing works! HELP!

---

### Post by Vaphell on 2009-09-08
it's not there or it doesn't install?

---

### Post by CyanPrime on 2009-09-09
> **Vaphell said:**
> it's not there or it doesn't install?
I don't know. Where would I find it?

---

### Post by 3rdalbum on 2009-09-09
```
sudo apt-get install libopenal1
```

If it's not there, make sure you have all the Ubuntu repositories enabled in the Software Sources program (Applications > Administration)

---

### Post by CyanPrime on 2009-09-09
Fixed. Used sudo apt-get install libopenal1

---

