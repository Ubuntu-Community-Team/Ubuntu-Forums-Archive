---
title: "Log files: brackets and .0's"
date: 2011-02-18
forum: General Help
---

### Post by PostScript on 2011-02-18
Hi there!

On startup, I get messages which look like this:

```
[   34.716443] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   34.716669] ata1.00: BMDMA stat 0x25
[   34.716789] ata1.00: failed command: READ DMA
[   34.716936] ata1.00: cmd c8/00:b8:70:60:23/00:00:00:00:00/e0 tag 0 dma 94208 in
[   34.716938]          res 51/40:4a:de:60:23/00:00:00:00:00/e0 Emask 0x9 (media error)
[   34.717439] ata1.00: status: { DRDY ERR }
[   34.717569] ata1.00: error: { UNC }
[   34.768306] ata1.00: configured for UDMA/100
[   34.768457] ata1: EH complete
[   41.473353] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   41.473566] ata1.00: BMDMA stat 0x25
[   41.473684] ata1.00: failed command: READ DMA
[   41.473829] ata1.00: cmd c8/00:b8:70:60:23/00:00:00:00:00/e0 tag 0 dma 94208 in
[   41.473831]          res 51/40:4a:de:60:23/00:00:00:00:00/e0 Emask 0x9 (media error)
[   41.474329] ata1.00: status: { DRDY ERR }
[   41.474458] ata1.00: error: { UNC }
[   41.524305] ata1.00: configured for UDMA/100
[   41.524451] ata1: EH complete
```What do the numbers in brackets mean? (I tried looking, but I don't know how to start to search for the answer to that without being too vague). I've noticed they're nearly always progressive (increasing). Do they just refer to the event number? And in my log file viewer, why is there a dmesg and a dmesg.0?

Thanks!

---

### Post by aeiah on 2011-02-18
arent they seconds since boot? thats what i always assumed. dmesg.0 is your prior dmesg log. you'll probably have a few.
```


[main ~] ls -al /var/log/dmesg*
-rw-r----- 1 root adm 44053 2011-02-18 07:51 /var/log/dmesg
-rw-r----- 1 root adm 44075 2011-02-17 09:08 /var/log/dmesg.0
-rw-r----- 1 root adm 12440 2011-02-15 08:11 /var/log/dmesg.1.gz
-rw-r----- 1 root adm 12511 2011-02-14 07:19 /var/log/dmesg.2.gz
-rw-r----- 1 root adm 12598 2011-02-12 09:56 /var/log/dmesg.3.gz
-rw-r----- 1 root adm 12540 2011-02-11 13:24 /var/log/dmesg.4.gz

```

note the dates, and note that after .0, they're compressed to save space as they get older.

---

### Post by PostScript on 2011-02-18
Ah, OK, thank you, that makes sense. But then what happens at [99999.999999999]? Does it just open a new dmesg log? Or start at zero? 99999 seconds is only twenty-seven hours, and I'm pretty sure some Ubuntuers here have their computers on for much longer than a day or two.

Thanks,

---

