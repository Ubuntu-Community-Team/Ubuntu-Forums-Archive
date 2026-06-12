---
title: "a question about startup programs"
date: 2010-09-10
forum: General Help
---

### Post by thelastblack on 2010-09-10
after some work i managed to get my modem working in ubuntu lucid but everytime i restart my computer i should use:
modprobe agrserial
(i need to user root access, sudo in my case)
cant i do something to make it run automatically at startup?
thx....

---

### Post by lukeiamyourfather on 2010-09-10
Add the module to the list in /etc/modules.conf file. Not tried in Ubuntu but that's how other distributions do it. Someone please chime in if Ubuntu is different.

---

