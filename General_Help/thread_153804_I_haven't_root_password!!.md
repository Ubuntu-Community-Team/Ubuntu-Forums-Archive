---
title: "I haven't root password!!"
date: 2006-04-01
forum: General Help
---

### Post by dont_know on 2006-04-01
hi! i've just installed kubuntu; it lasted veery much. however it didn't ask me what packages i wanted. what has really annoyed me is that it didn't request for root's password, just users'. i've tryed with none, "default", "kubuntu" with no succeed. what should i do??!! thankx for advices!

---

### Post by aysiu on 2006-04-01
There is no root password.

Read more here:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by dont_know on 2006-04-02
uh? so any user could be able to use root privileges calling sudo? no way! i've found the ```
sudo passwd root
``` command, that will active root account. thanks for reply.

---

### Post by bertpatt on 2006-04-02
As far as I'm concerned it's wise to create a root password.
I altered a config file to do with root and made a typing error, so everytime I tried to go into root with sudo, I couldn't because of the typing error.
So I couldn't edit out the error.
But because I had created a root password I was able to su and then edit out the error.
Saved my bacon!!!

---

### Post by aysiu on 2006-04-02
You can always boot into recovery mode.
Or use a live CD for recovery.

---

### Post by Gustav on 2006-04-02
[QUOTE=dont_know]uh? so any user could be able to use root privileges calling sudo? no way! i've found the ```
sudo passwd root
``` command, that will active root account. thanks for reply.[/QUOTE]
No, not any user. Just the first user and the other users you add to the "admin" group. I like the sudo model much better than su (even though I hated it at the start)

---

### Post by mexlinux on 2006-04-04
Why are you guys so comlicated to open a root console...
sudo -s
Thats it

---

### Post by wcks48 on 2006-04-05
wow, that's great. thanks guy!

---

### Post by take_one on 2006-04-05
i also got the same problem. this is how i fixed it.

sudo -s
then
passwd
to set your password

i hope it helps

---

