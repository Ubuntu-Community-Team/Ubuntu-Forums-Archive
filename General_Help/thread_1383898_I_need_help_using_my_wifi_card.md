---
title: "I need help using my wifi card"
date: 2010-01-17
forum: General Help
---

### Post by JeremyR0491 on 2010-01-17
i have an hp pavilion dv6605us laptop and i installed the latest version of ubuntu but i cant use my wifi card.

ive searched up other instructions and one told me to go to System/Admin/Hardware drivers and i did and no hardware came up at all.

---

### Post by bkratz on 2010-01-17
> **JeremyR0491 said:**
> i have an hp pavilion dv6605us laptop and i installed the latest version of ubuntu but i cant use my wifi card.

ive searched up other instructions and one told me to go to System/Admin/Hardware drivers and i did and no hardware came up at all.




Try going to the terminal

Applications>>Accessories>>Terminal
and type in:

lspci | grep Wireless
(that is LSPCI in lowercase)
And copy/paste the output back here. If you don't see anything try
lspci

---

### Post by rogue_0111 on 2010-01-17
This thread may be of some help:

[http://ubuntuforums.org/archive/index.php/t-764999.html](http://ubuntuforums.org/archive/index.php/t-764999.html)

Good luck

---

### Post by gabak on 2010-01-17
go to terminal and type lspci and tell me what kinda wifi card you got then i can help u.

---

### Post by JeremyR0491 on 2010-01-17
> **gabak said:**
> go to terminal and type lspci and tell me what kinda wifi card you got then i can help u.

this is the type of wifi card i have
Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)

---

### Post by bkratz on 2010-01-18
> **JeremyR0491 said:**
> this is the type of wifi card i have
Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)



See this thread

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

