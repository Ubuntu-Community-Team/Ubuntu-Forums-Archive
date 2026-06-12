---
title: "Problems with Ubuntu 10.04 LTS and Evolution 2.28.3"
date: 2011-12-15
forum: General Help
---

### Post by joaotoscano on 2011-12-15
Hi everybody

Evolution receives messages, but won't send email.
I'm using Ubuntu 10.04 LTS and Evolution 2.28.3
I think I set it up properly, ie.. outgoing smtp.live.com

Ive googled for the solution with no success, and couldn't find an answer doing a search in Ubuntuforums. What could possibly be wrong?

Joao Toscano

---

### Post by lechien73 on 2011-12-15
If you're sending through smtp.live.com, then this requires authentication with your Windows Live username and password. You also need to set it to a secure SSL connection, and change the outgoing port from 25 to 587.

---

### Post by joaotoscano on 2011-12-15
> **lechien73 said:**
> If you're sending through smtp.live.com, then this requires authentication with your Windows Live username and password. You also need to set it to a secure SSL connection, and change the outgoing port from 25 to 587.


well so far your post did not help but i am looking forward to have a solution for this :P

here is the screenshot making the changes you said ...

[IMG]http://i42.servimg.com/u/f42/11/22/20/87/shot210.jpg[/IMG]

---

### Post by lechien73 on 2011-12-16
There was a thread about this a while ago. Could you try the fix suggested here: [http://ubuntuforums.org/showthread.php?t=938366&page=2#16](http://ubuntuforums.org/showthread.php?t=938366&page=2#16)

---

