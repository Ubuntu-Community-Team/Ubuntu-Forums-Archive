---
title: "Few more of my paprecuts need solution"
date: 2009-11-13
forum: General Help
---

### Post by sigurnjak on 2009-11-13
1 . I have user account i do not use any more . So i removed user and matching home folder yet it still shows up on my login screen . How do i remove it from the list ?

2. Every once in a while we receive cute  .pps file . Sometimes i wish to extract images . As of recently OO-Impress goes directly to slide and does not give me option to view it witout playing slide shoe . How do i prevent it from going in to slide show ?

Btw , i am using Karmic if  that makes any difference .

---

### Post by delcypher on 2009-11-13
1.I found that the GUI tools didn't work at all for removing an old user account on my system.

Running the following did the job

```
sudo deluser --remove-home username
```

Where username is the username you wish to remove.

2. Sorry I don't use Impress so I can't provide any input there.

---

### Post by sigurnjak on 2009-11-13
Thank you very much ! That worked great , it is going in to my tip collection ! 

Viva la CLI !!!!:p

---

### Post by sigurnjak on 2009-11-14
If i rename a .pps into .ppt, you can then edit it.

Ah , wonders of Google .

---

