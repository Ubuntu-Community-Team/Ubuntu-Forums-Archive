---
title: "/etc/apt/sources.list help"
date: 2010-12-17
forum: General Help
---

### Post by zealibib slaughter on 2010-12-17
Hi everyone.  I got a dumb question.  I been trying to fix some dependency problems and stupidly changed the file permissions of /etc/apt/sources.list.  My problem is I don't remember the correct file permissions. Is it 4-4-4 as in I would code chmod 444 to change it back to root access only or is it something else?

---

### Post by Elfy on 2010-12-17
-rw-r--r-- 1 root root 2621 2010-12-17 07:21 /etc/apt/sources.list

needs to be writable

---

### Post by Linyx on 2010-12-17
[SIZE="2"]And what about this:-

sudo chmod 644 /etc/apt/sources.list[/SIZE]
[SIZE="2"][/SIZE]
[SIZE="2"]It will allow to to **read+write** and others can **only ****read** your sources.list[/SIZE]

---

### Post by zealibib slaughter on 2010-12-17
Thanks for the answers.  I couldnt remember which only allowed root to write.  Both replies helped alot.

---

