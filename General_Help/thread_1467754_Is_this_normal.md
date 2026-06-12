---
title: "Is this normal?"
date: 2010-05-01
forum: General Help
---

### Post by abbood99 on 2010-05-01
I am upgrading from Ubuntu 9.10 to Ubuntu 10.04 using the update manager. This window has not changed for half an hour. But it's not frozen. I can drag and move it.

Upgrade manager window:
(click to enlarge)
[ATTACH]154914[/ATTACH]

My processes are as follows:
(click to enlarge)
[ATTACH]154915[/ATTACH]



Your help is appreciated

---

### Post by bcbc on 2010-05-01
press CTRL+C

That happened to me as well. Then it will continue.

---

### Post by abbood99 on 2010-05-01
Thanks this worked and it's continuing again. I hope it works till the end and restarts without hassle :)

---

### Post by bcbc on 2010-05-01
> **abbood99 said:**
> Thanks this worked and it's continuing again. I hope it works till the end and restarts without hassle :)

Well you could have waited but I suspect you would have waited a long time ;)

But seriously, it completed fine for me and others as well. So you should be good to go.

---

### Post by bcbc on 2010-05-01
When it asks you where to install grub, don't select any partitions. Only the drive MBR. If you have one drive that's /dev/sda

If you're updating a wubi install, then don't install grub2 to the drive at all.

---

### Post by rpjames on 2010-05-14
Question: my installation is stuck in the same place. When I hit CTRL-C I see a popup message that says: 

"This will abort the operation and may leave the system in a broken state. Are you sure you want to do that?"

Are you saying that you clicked "Yes" at this point and things worked?

---

