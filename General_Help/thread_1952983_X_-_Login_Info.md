---
title: "X - Login Info"
date: 2012-04-05
forum: General Help
---

### Post by kolke on 2012-04-05
Hello Guys,

when I log into a X-session a string appears which says something like "Testing reasons". I remember that I edited something like that, but i cant find the file in which i can change those settings.

Searched in /etc via "find" and "grep"...no results.
So does anyone know where you can set those X-login-settings? It must be just a little echo command...

Overmore it'd be interesting to know which possible ways there are to find out on which files the program (X-session) refers. I just recently read something about ELF-Datas + the objdump and the readelf programm.
With the help of those programs, is it possible to find out where this string is at?
If yes please tell me. Or any other way.

Thx in advance for your help!
kolke

---

### Post by 2F4U on 2012-04-05
Do you mean by any chance the virtual console configurations (tty1 to tty6)? These can be found in /etc/init/ttyx.conf where x=1 ... 6.

---

