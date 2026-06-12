---
title: "Permissions Deniedt/lightning"
date: 2011-05-19
forum: General Help
---

### Post by Sweet_Mafia on 2011-05-19
I have the latest version of ubuntu for 64-bit. I added a new user called "ventrilo" and add my ventrilo files inside. Of course I installed the 32-bit libraries for ventrilo, as it only supports 32-bit.

From their I logged in as ventrilo through shh, and tried "./ventrilo_srv"

I get this error. How to fix that?
> 
ventrilo@Viligant-Gaming:~$ ./ventrilo_srv
-bash: ./ventrilo_srv: Permission denied


---

### Post by jerrrys on 2011-05-20
try **sudo** ./ventrilo_srv

---

### Post by 3rdalbum on 2011-05-20
> **jerrrys said:**
> try **sudo** ./ventrilo_srv

No; you should definitely not run an internet-facing server as root!

The reason why the error message is appearing is because you haven't given the file the "execute permission". Basically, right-click on the file, go to Properties and then to Permissions, and click "Allow file to execute as a program".

---

### Post by jerrrys on 2011-05-20
thanks for setting me straight on that 3rdalbum

---

