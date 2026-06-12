---
title: "wireless adaptor"
date: 2010-02-25
forum: General Help
---

### Post by spiky001 on 2010-02-25
hi i have just installed ubuntu i,m having trouble with my wireless device, how do i find out what 1  is installed

---

### Post by PoHandle on 2010-02-25
Open a terminal and enter```
lspci | grep -i 'wireless'
``` and the output should tell you what hardware you have.

If there is no output from that, you can try
```
lspci | grep -i 'ethernet'
```
which will also display your wired NIC.

---

### Post by spiky001 on 2010-02-25
thks now just got to work out getting it to work lol

---

### Post by pbrane on 2010-02-25
Post back with the type of wireless card you have. I'm sure someone may be able to help you.

---

### Post by spiky001 on 2010-02-25
i,m gonna try google & sort it myself 1st, might be back with a disaster lol but thks anyway

---

