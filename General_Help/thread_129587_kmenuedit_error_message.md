---
title: "kmenuedit error message"
date: 2006-02-14
forum: General Help
---

### Post by wizzkid on 2006-02-14
Guys, I installed Dia on my Kubuntu 5.10 Brezzy, after installing I checked the  looking for dia icon, i found out that it didnt appear on my menu, but when I type it in terminal "dia" it works. I tried adding it manually using keditmenu on terminal, but when I save the changes I made, terminal show this error message:

Error: "/var/tmp/kdecache-noel" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
ERROR: Communication problem with kmenuedit, it probably crashed.
wizz@wizzl:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x30003e4
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3001020
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x30016b1


thus, the changes i made didnt apply on my menu. I used sudo kmenuedit and without sudo, it does the same thing. hope somebody could help me.

Thanks.

---

### Post by wizzkid on 2006-02-15
Hi, the error still exist when I run it. on terminal I typed sudo kmenuedit, and i encounter this error.

wizz@wizzl:~$ sudo kmenuedit
Password:
Error: "/var/tmp/kdecache-noel" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
ERROR: Communication problem with kmenuedit, it probably crashed.
wizz@wizzl:~$

Hope somebody could help

TY

---

