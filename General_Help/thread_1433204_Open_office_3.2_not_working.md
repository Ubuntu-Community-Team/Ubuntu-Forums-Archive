---
title: "Open office 3.2 not working"
date: 2010-03-18
forum: General Help
---

### Post by kut77less on 2010-03-18
I installed open office 3.2, but when I start it get this error 

> /opt/openoffice.org3/program/soffice.bin: /opt/openoffice.org3/program/libuno_sal.so.3: version `UDK_3.10' not found (required by /opt/openoffice.org3/program/../basis-link/program/libsfxlx.so)
/opt/openoffice.org3/program/soffice.bin: /opt/openoffice.org3/program/../basis-link/program/../ure-link/lib/libxml2.so.2: no version information available (required by /opt/openoffice.org3/program/libjvmfwk.so.3)
 

Does anybody know how to fix this?

Thanks

---

### Post by Hagar Delest on 2010-03-20
How have you installed OOo?
Check that one for example: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by kut77less on 2010-03-21
> **Hagar de l'Est said:**
> How have you installed OOo?
Check that one for example: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

I did that, and, when I attempted to start the program I got this error 


> /opt/openoffice.org3/program/soffice.bin: /opt/openoffice.org3/program/libuno_sal.so.3: version `UDK_3.10' not found (required by /opt/openoffice.org3/program/../basis-link/program/libsfxlx.so)
/opt/openoffice.org3/program/soffice.bin: /opt/openoffice.org3/program/../basis-link/program/../ure-link/lib/libxml2.so.2: no version information available (required by /opt/openoffice.org3/program/libjvmfwk.so.3)




What should I do?

---

### Post by Hagar Delest on 2010-03-22
Strange. I've seen that only once here: [[Solved] OpenOffice 3 fails to start]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=10766"). Perhaps Google will give you some additional hints.

---

### Post by kut77less on 2010-03-23
> **Hagar de l'Est said:**
> Strange. I've seen that only once here: [[Solved] OpenOffice 3 fails to start]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=10766"). Perhaps Google will give you some additional hints.


I did that, but still no luck.

---

### Post by linden940 on 2010-03-23
install and reinstall....see if that will help

maybe something messed up during the installing of open office

---

### Post by kut77less on 2010-03-23
> **linden940 said:**
> install and reinstall....see if that will help

maybe something messed up during the installing of open office


It worked!! This time I went to the opt dictionary, and deleted all the openoffice folders. Thanks to all those who helped.

---

