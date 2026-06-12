---
title: "how to uninstall postfix"
date: 2006-04-24
forum: General Help
---

### Post by jeisma on 2006-04-24
hi!

how do you uninstall postfix? when i installed mysql server. postfix was also installed. when i try to apt-get remove postfix, system says mysql will also be removed.

any tips?

thanks!

---

### Post by DoeRayMe on 2006-04-24
mysql depends on postfix

if you try and remove postfix, mysql will get removed also

---

### Post by jeisma on 2006-04-24
[QUOTE=DoeRayMe]mysql depends on postfix

if you try and remove postfix, mysql will get removed also[/QUOTE]

ah ok.

for a while i thought they should be totally different package.

thanks for the clarification!

---

