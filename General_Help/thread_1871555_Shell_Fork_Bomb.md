---
title: "Shell Fork Bomb"
date: 2011-10-29
forum: General Help
---

### Post by marcusww on 2011-10-29
Hi   I recently had a (benign?) shell fork bomb incident, which I managed to correct with this command:    while (sleep 100 &!) do; done  However, my server now shows this document in my user directory, which was created at the time of the shell bomb:  sedd6GOTx  Anybody know what this might be?  I can't delete it nor can I open it with a text editor

---

### Post by TeoBigusGeekus on 2011-10-29
Try with
```
file ~/sedd6GOTx
```
to find out what kind of file it is.

---

### Post by Habitual on 2011-10-29
```
strings ~/sedd6GOTx | less
```

---

