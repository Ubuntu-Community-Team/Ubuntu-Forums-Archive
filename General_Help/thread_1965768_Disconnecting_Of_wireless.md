---
title: "Disconnecting Of wireless"
date: 2012-04-26
forum: General Help
---

### Post by sani786 on 2012-04-26
Hy every body,

I have install Wireless on my laptop but it become disconnect and not connect till i restart my computer after restarting then Wif connect 

ANY help??????:confused:

---

### Post by raja.genupula on 2012-04-26
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
dmesg | grep -i wlan
ifconfig -a
iwconfig
rfkill list all
```

post the output of this.

---

