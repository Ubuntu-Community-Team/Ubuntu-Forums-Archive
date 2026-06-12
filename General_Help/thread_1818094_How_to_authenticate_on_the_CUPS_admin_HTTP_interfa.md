---
title: "How to authenticate on the CUPS admin HTTP interface"
date: 2011-08-04
forum: General Help
---

### Post by ofnuts on 2011-08-04
I can connect to the HTTP cups interface (localhost:631) but if I need admin priviledges, giving my id/pwd doesn't work. I don't see any "cups" group defined.

Otherwise, how do I enable a printer? I could disable it using the KDE printer management interface, but I can't re-enable it using same... Answer: /usr/sbin/cupsenable

---

### Post by SeijiSensei on 2011-08-04
I think Kubuntu 10.10 enables you to use your own username and password to authenticate if you also have sudo privileges.  In earlier versions I recall having problems accessing the administrative functions from the web interface.

You can also try launching the browser by typing "kdesudo firefox" at a command prompt.

Otherwise the only option is to have an active root account.  You're [on your own]("http://ubuntuforums.org/showthread.php?t=1486138") about this approach, though.

---

