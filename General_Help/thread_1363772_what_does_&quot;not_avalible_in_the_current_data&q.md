---
title: "what does &quot;not avalible in the current data&quot; mean in the Ubuntu software center?"
date: 2009-12-24
forum: General Help
---

### Post by bnr18241 on 2009-12-24
every software i went to said this

---

### Post by howefield on 2009-12-24
Try opening a terminal (Applications > Accessories > Terminal) and type

```
sudo apt-get update
```

Then try again to use the software center.

---

### Post by bnr18241 on 2009-12-24
it says command not found

---

### Post by bnr18241 on 2009-12-24
nevermind

---

### Post by PsychoDevon on 2009-12-24
Aaah. This happens to me whenever I reinstall Ubuntu Karmic with Wubi.

First, obviously connect to the internet (if you're not using Ubuntu to post this) in Ubuntu.

Then go to System>Administration>Update Manager

Check for and install all updates.

Then, wait and restart if it tells you to. Even if it doesn't, it's a good idea to anyway.

Then, after restarting, try installing with the Software Center again. It should work now.

---

