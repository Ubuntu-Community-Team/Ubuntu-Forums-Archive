---
title: "Accedintally Deleted &quot; LoginWindow&quot; from gdm directory"
date: 2010-12-18
forum: General Help
---

### Post by hamzamusa on 2010-12-18
hello ,

i accidentally deleted "LoginWindow" directory from 
```

/usr/share/gdm/autostart/LoginWindow
```

now i can't get into login window ......

how i can fix this problem , or undo this mistake " should i need a time machine " ?

:cry: :?

---

### Post by lmarmisa on 2010-12-18
What is your Ubuntu version?.

---

### Post by hamzamusa on 2010-12-18
> **lmarmisa said:**
> What is your Ubuntu version?.
Ubuntu 10.10

---

### Post by lmarmisa on 2010-12-18
I attach a file named LoginWindow.tar.gz with the contents of the deleted directory. The contents belong to Ubuntu 10.10 Desktop 32 bits.

You will need to copy this file to the folder **/user/share/gdm/autostart **(you will need root privileges).

Then type these commands:

```

sudo bash
cd /usr/share/gdm/autostart
gzip -d LoginWindow.tar.gz
tar xvf LoginWindow.tar

```

---

### Post by hamzamusa on 2010-12-18
> **lmarmisa said:**
> I attach a file named LoginWindow.tar.gz with the contents of the deleted directory. The contents belong to Ubuntu 10.10 Desktop 32 bits.

You will need to copy this file to the folder **/user/share/gdm/autostart **(you will need root privileges).

Then type these commands:

```

sudo bash
cd /usr/share/gdm/autostart
gzip -d LoginWindow.tar.gz
tar xvf LoginWindow.tar

```
hey thank you very much , it worked thanks for your help

:D

---

### Post by lmarmisa on 2010-12-18
Great!!!. :D

Please, mark the thread as SOLVED.

---

### Post by udaykiran on 2011-03-30
Hi, I'm facing a same problem. I actually accidentally deleted even the autostart folder. Now it shows a dark blank screen after the boot up. Is there any solution to this? I mean I've the LoginWindow which you posted here.. but I can't figure out a way to copy it into the folder.. Please help me out.

---

### Post by baihegen on 2011-03-30
it Looks interesting. And i Never tried.

---

