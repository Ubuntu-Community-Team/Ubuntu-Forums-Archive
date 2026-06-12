---
title: "SImple Lamp question"
date: 2006-04-18
forum: General Help
---

### Post by evillawngnome on 2006-04-18
"Your PHP installation appears to be missing the MySQL which is required for WordPress."

Im missing an apt-get step here, i think. Anyone know the name of the package(s) i need?

---

### Post by cgjones on 2006-04-18
Trying installing mysql-server or mysql-server-4.1
For example:

apt-get install mysql-server

I'm not currently running Ubuntu, so I couldn't verify this first hand, but I think this might help. If not, check out one of the the php-mysql modules. There are different versions, depending on what version of PHP you are using.

---

