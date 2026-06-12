---
title: "mysql.sock"
date: 2006-01-20
forum: General Help
---

### Post by oly on 2006-01-20
i am trying to setup odbc with mysql, however i keep getting an error about a mysql.sock file, i guessed this could be a path issue, but i have searched the computer using slocate and Find Files gui program, does it exist ??

has it been renamed / what can i do anyone able to point me in the right direction ??

---

### Post by oly on 2006-01-25
seems this does not exist, however commenting out the line that refers to mysql.sock fixed the problem it then just uses the tcp stack i believe.

this files only seems to be for local access with out tcp if it exists.

---

