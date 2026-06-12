---
title: "firefox strange bug in karmic??"
date: 2009-12-03
forum: General Help
---

### Post by abhilashm86 on 2009-12-03
my firefox went blank for time,  mouse and other keys were working, but firefox dead!!
so i tried kill process and started to search its PID ? damn not possible by htop or top or ps or system monitor??

when i went to start firefox again, strange error, firefox not booting?? but other applications working fine..........
i restarted computer to correct this:(

when i tried opening firefox in terminal, 
ERROR--> SEGMENTATION FAULT !!

how can i recover?? please help me, give reasons and tell how to overcome and start firefox without restart computer??

---

### Post by openuniverse on 2009-12-03
.

---

### Post by fluffman86 on 2009-12-03
also backup and delete your ~/.mozilla

---

### Post by abhilashm86 on 2009-12-03
> **openuniverse said:**
> have you tried removing ff and reinstalling it with synaptic?

is this required?? what version of ff will be installed then? currently my ff version is ```
abhilash@abhilash:~$ firefox -v
Mozilla Firefox 3.5.5, Copyright (c) 1998 - 2009 mozilla.org
abhilash@abhilash:~$ 

```

---

### Post by Ancanus on 2009-12-03
> **abhilashm86 said:**
> my firefox went blank for time,  mouse and other keys were working, but firefox dead!!
so i tried kill process and started to search its PID ? damn not possible by htop or top or ps or system monitor??

when i went to start firefox again, strange error, firefox not booting?? but other applications working fine..........
i restarted computer to correct this:(

when i tried opening firefox in terminal, 
ERROR--> SEGMENTATION FAULT !!

how can i recover?? please help me, give reasons and tell how to overcome and start firefox without restart computer??

You can close a process by using *pkill* and referring to the process by its name, as in
```

pkill firefox
```

---

### Post by abhilashm86 on 2009-12-04
> **Ancanus said:**
> You can close a process by using *pkill* and referring to the process by its name, as in
```

pkill firefox
```

oh never knew this!! gonna try now, thanks a lot friend:)

---

