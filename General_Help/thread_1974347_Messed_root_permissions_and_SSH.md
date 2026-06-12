---
title: "Messed root permissions and SSH"
date: 2012-05-05
forum: General Help
---

### Post by albertdiones on 2012-05-05
Hi,

  On my ubuntu VPS, I mistakenly executed `chmod 0770 . -R` while I'm on the / dir

  I tried to recover  by chmod'ing all to 0755, but now I can't connect through normal SSH, without even asking for username.

  Can anybody lead me to right direction on fixing this?

  Thanks in advance :)

---

### Post by Cheesemill on 2012-05-06
Re-install the OS from scratch.

It may sound a bit over the top but the problem that you are facing is that certain files require certain permissions for the system to run properly, there isn't one set of permissions that you can quickly apply to the entire machine that will get it to work properly again.

It is possible to change the permissions of all files back to what they should be one by one but first you would have to know what these permissions are and second, it would take you days to do so.

---

### Post by albertdiones on 2012-05-12
Hey! Thanks for your reply, sorry for the late reply,

Luckily I fixed this, I just backed up my ssh config and used this:
```
dpkg-reconfigure openssh-server
```


I hope it can help anyone in the future

Have a good day! :)

---

