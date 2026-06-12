---
title: "APT Package Install Error (/var/lib/dpkg/)"
date: 2010-05-17
forum: General Help
---

### Post by Max Avion on 2010-05-17
Hello,

I am running Ubuntu 9.10 (Karmic) and have recently noticed an error message at the terminal whenever I attempt to install a package with the apt-get command.

```

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

I am not able to install or remove any applications, as it keeps giving me this message. If anyone is able to provide me with some guidance, would be very much appreciated. Thank you in advance. 

Regards,
Max

---

### Post by angry_johnnie on 2010-05-17
try

```
sudo dpkg --configure -a
```

---

