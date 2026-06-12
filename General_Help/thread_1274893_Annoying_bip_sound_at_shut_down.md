---
title: "Annoying bip sound at shut down"
date: 2009-09-25
forum: General Help
---

### Post by fasoulas on 2009-09-25
How can remove the bip sound in 9.04 that sounds when ubuntu shuts down?

---

### Post by MelDJ on 2009-09-25
go to sound then system beep and uncheck system enable system beep

---

### Post by fasoulas on 2009-09-25
> **MelDJ said:**
> go to sound then system beep and uncheck system enable system beep

I haven't found the system beep you wrote in sound properties but i fix it with another way 

sudo gedit /etc/modprobe.d/blacklist.conf

and then add in the text file the following line

blacklist pcspkr

---

### Post by MelDJ on 2009-09-25
glad you fixed it though:KS

---

### Post by credobyte on 2009-09-25
> **MelDJ said:**
> go to sound then system beep and uncheck system enable system beep

9.04 doesn't have this option. You need to blacklist it manually.

---

