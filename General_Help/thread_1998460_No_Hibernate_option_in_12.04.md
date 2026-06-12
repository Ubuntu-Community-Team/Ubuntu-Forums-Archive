---
title: "No Hibernate option in 12.04"
date: 2012-06-06
forum: General Help
---

### Post by furmada on 2012-06-06
Hello,

I did a fresh install of 12.04 on my Acer Aspire One netbook.
There is now no Hibernate option in the system menu, power off menu, or Power options. This is not too critical, but Hibernation is very helpful at times. 

Thank You

---

### Post by Toz on 2012-06-06
Hibernate has been disabled by default in Ubuntu 12.04. See the "Get hibernate back" section of this page for more information: [http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html]("http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html").

---

### Post by furmada on 2012-06-09
when I type pm-hibernate I get msg "not enough free swap" in system Monitor, swap is marked as 1011.0 MiB. Is this enough to hibernate?

---

### Post by tumutanzi.com on 2012-06-09
If I have not seen your report, I would never notice there is such a bug. I have a Acer netbook too.

---

### Post by Toz on 2012-06-09
> **furmada said:**
> when I type pm-hibernate I get msg "not enough free swap" in system Monitor, swap is marked as 1011.0 MiB. Is this enough to hibernate?

You need to have enough swap space to hold the contents of ram. Some that the swap should be 1.5x the amount of ram. How much ram does your system have?

---

