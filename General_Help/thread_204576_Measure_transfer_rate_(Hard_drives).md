---
title: "Measure transfer rate (Hard drives)"
date: 2006-06-27
forum: General Help
---

### Post by Poka64 on 2006-06-27
Is there a way to measure the transfer rates on my hard drives ?

---

### Post by Ramses de Norre on 2006-06-27
```
sudo hdparm -tT /dev/???
``` ;)

---

### Post by Poka64 on 2006-06-27
Thx ! :)

---

### Post by Poka64 on 2006-06-27
is this a "normal" rate for sata drives on linux ?

/dev/sda1:
 Timing cached reads:   2900 MB in  2.00 seconds = 1449.91 MB/sec
 Timing buffered disk reads:  168 MB in  3.00 seconds =  56.00 MB/sec

/dev/sdb1:
 Timing cached reads:   2428 MB in  2.00 seconds = 1213.92 MB/sec
 Timing buffered disk reads:  144 MB in  3.03 seconds =  47.55 MB/sec

---

### Post by Ramses de Norre on 2006-06-27
These are mine (hda is ata drive, sda sata): ```
ramses@icarus:~$ sudo hdparm -tT /dev/hda /dev/sda

/dev/hda:
 Timing cached reads:   2796 MB in  2.00 seconds = 1397.91 MB/sec
 Timing buffered disk reads:  164 MB in  3.00 seconds =  54.59 MB/sec

/dev/sda:
 Timing cached reads:   2932 MB in  2.00 seconds = 1465.91 MB/sec
 Timing buffered disk reads:  176 MB in  3.02 seconds =  58.35 MB/sec

```
I've got a couple programs running which influences the ratings but it gives you an idea;)

EDIT: check out man hdparm for ways to increase the speed, many of them can lead to higher chances of data corruption though..

---

### Post by Poka64 on 2006-06-27
cool, I seem to have the same rates (almost)

/dev/sdb1:
 Timing cached reads:   3012 MB in  2.00 seconds = 1505.91 MB/sec
 Timing buffered disk reads:  196 MB in  3.02 seconds =  64.90 MB/sec

---

### Post by denisesballs on 2006-06-30
That's about where I am too. Shouldn't the SATA get up to 160mb/s though?

---

### Post by slackern on 2006-06-30
[QUOTE=denisesballs]That's about where I am too. Shouldn't the SATA get up to 160mb/s though?[/QUOTE]

The SATA(1)-150 Interface and the SATA(2)-300 are capable of it but the physical discs can't utilize all the bandwidth in the interfaces yet.

---

