---
title: "Unable to adminstrate users"
date: 2009-10-12
forum: General Help
---

### Post by kehon on 2009-10-12
The System -> Adminstator -> Users and Groups has the unlock button that does nothing so I cannot change permissions thru a gui

---

### Post by Iowan on 2009-10-12
Are you logged in as an administrator (sudoer)?
Meaning... does your user have **sudo** privileges?

---

### Post by kehon on 2009-10-12
yeah i can use sudo on the command line to run apps as root. i tried running sudo users-admin and it was still locked

edit: also is it normal that i should need to be root to modify files on an apache server. I would just change the permissions but i think it might be a security risk

---

### Post by Iowan on 2009-10-12
> **kehon said:**
> edit: also is it normal that i should need to be root to modify files on an apache server. I would just change the permissions but i think it might be a security riskA bit off-topic, but...
It depends which files - the "usual" place for files is */var/www* (which is owned by root). [This ]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts") help page mentions moving/changing **DocumentRoot** and **Directory**.

---

### Post by CharlesA on 2009-10-12
> **kehon said:**
> The System -> Adminstator -> Users and Groups has the unlock button that does nothing so I cannot change permissions thru a gui

That happens to me when I am connected with VNC. No idea why and I haven't been able to find any info about it. :confused:

---

