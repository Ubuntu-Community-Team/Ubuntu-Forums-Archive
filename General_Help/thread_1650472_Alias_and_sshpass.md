---
title: "Alias and sshpass"
date: 2010-12-21
forum: General Help
---

### Post by Screatch on 2010-12-21
I am trying to make an alias out of sshpass command (sshpass is a tool to make logging into a server only with a password).

Command itself looks something like this and works perfectly well by itself, but when i try to make alias out of it, it goes all wrong.

alias servername='sshpass -p '<7f%97BcA!/' ssh root@serverip'

then i restarted .bashrc, tried out my alias and i got
bash: 7f%97BcA!/ ssh root@serverip: No such file or directory

I figured out it's because of "<" symbol in the password, is there anyway to make alias ignore this symbols and just make him think its part of password, not as some command for alias, without me changing the server password.

Thanks in advance.

---

### Post by Screatch on 2010-12-23
Found a solution, add / before character.

---

