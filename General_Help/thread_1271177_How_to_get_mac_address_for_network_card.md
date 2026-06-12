---
title: "How to get mac address for network card?"
date: 2009-09-20
forum: General Help
---

### Post by funfeast on 2009-09-20
Dear Friends,

I am new to this OS. trying to learn and use it with may day to day work.
By mistake i deleted mac address in network setting. how to get that mac address back. 

due to no mac address i am not able to set certain settings.
Please help me in this issue.

Regards,
Niraj

---

### Post by t0p on 2009-09-20
Open a terminal and type:

```
ifconfig
```

This will get you a list of your network interfaces, including mac address ("HWaddr") of the card in question.

---

### Post by PurposeOfReason on 2009-09-20
```
sudo ifconfig -a
```

The numbers after HWaddr, top line.

---

### Post by nikhilbhardwaj on 2009-09-20
i'm not sure that you can actually delete the mac address
however _**ifconfig**_ lists out the most of the networking options

---

