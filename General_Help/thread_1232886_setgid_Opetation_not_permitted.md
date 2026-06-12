---
title: "setgid: Opetation not permitted"
date: 2009-08-06
forum: General Help
---

### Post by sitex on 2009-08-06
[SIZE=2]I gave following command to change permission[/SIZE]
[SIZE=3][COLOR=Sienna]chmod -R 777 /*[/COLOR][/SIZE]
after that I can not log as root
when i try to log as root, I have got an error like

[SIZE=3][COLOR=Red]setgid: Operation not Permitted[/COLOR][/SIZE]

please help...

---

### Post by ibutho on 2009-08-06
Hi and welcome to the forums. It seems like you ruined you filesystem permissions by making everything read, writable and executable by everyone. Some apps and files expect specific permissions and if those permissions aren't right then your system may not work right. I can't think of a way to rememdy your problem other than a reinstall.

---

### Post by sitex on 2009-08-06
Thanks very much for your reply. I understood my fault.

---

