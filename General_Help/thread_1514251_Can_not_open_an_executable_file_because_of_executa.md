---
title: "Can not open an executable file because of executable bit"
date: 2010-06-20
forum: General Help
---

### Post by digitalphoenix10 on 2010-06-20
I am running into a snag on .exe files in Lucid. I have Wine installed, but I can not open the file as it is blocked from executing with a window popping up telling me that this file was blocked due to security reasons. I go into the files properties and try to change the permission but that does not help. Is there a way to get around this? Possibly in the terminal as root?

---

### Post by megamandos on 2010-06-20
yes, in terminal as root.

navigate to the file and type the command:

sudo chmod 0755 <your file name>

---

### Post by digitalphoenix10 on 2010-06-20
Is there also a way to do this but with a data CD?

---

### Post by steveneddy on 2010-06-20
> **digitalphoenix10 said:**
> Is there also a way to do this but with a data CD?

Copy the file from the CD to your desktop.

:roll:

---

