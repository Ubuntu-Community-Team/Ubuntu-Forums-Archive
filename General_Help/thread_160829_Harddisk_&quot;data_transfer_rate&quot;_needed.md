---
title: "Harddisk &quot;data transfer rate&quot; needed?"
date: 2006-04-15
forum: General Help
---

### Post by 2rB on 2006-04-15
Searched around the forum, but can't find an answer to my problem.

I'm going to do an Ubuntu-installation, and was looking trough the hardware, and discovered that my SCSI-contoller's data transfer rate only is 20 mb/s.

Does anybody know how much, and in what ways, this will affect the system?
Is it recomended to get another SCSI-controller?

---

### Post by Ramses de Norre on 2006-04-15
What os are you running now? I think if that runs at a decent speed, ubuntu will be tuneable enough to get at least equal performance.

---

### Post by 2rB on 2006-04-15
My controller is in the box - never been used...
Just been laying there...

---

### Post by Ramses de Norre on 2006-04-15
I'd give it a shot then. If it goes too slow you can buy a new one.
My IDE disk: ```
 Timing cached reads:   1776 MB in  2.00 seconds = 887.25 MB/sec
 Timing buffered disk reads:   82 MB in  3.10 seconds =  26.46 MB/sec

``` for reference and you can do with a lot slower too.

---

### Post by dcstar on 2006-04-15
[QUOTE=Ramses de Norre]I'd give it a shot then. If it goes too slow you can buy a new one.
My IDE disk: ```
 Timing cached reads:   1776 MB in  2.00 seconds = 887.25 MB/sec
 Timing buffered disk reads:   82 MB in  3.10 seconds =  26.46 MB/sec

``` for reference and you can do with a lot slower too.[/QUOTE]
And my old UDMA5 7200 RPM IDE disk is:
```
/dev/hda:
 Timing cached reads:   1240 MB in  2.00 seconds = 618.88 MB/sec
 Timing buffered disk reads:  164 MB in  3.03 seconds =  54.10 MB/sec
```

---

