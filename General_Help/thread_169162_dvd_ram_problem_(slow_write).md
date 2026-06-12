---
title: "dvd ram problem (slow write)"
date: 2006-05-02
forum: General Help
---

### Post by Selmi on 2006-05-02
i tried to work with dvd ram.

what i did is that i installed udftools, 
using pktsetup i assigned /dev/dvdram to /dev/dvd
into fstab i wrote that /dev/dvdram mounts to /media/dvdram

as root i can mount /media/dvdram and content of dvdram is both readable and writeable. but writing is terribly slow. speed is about 600kb/s. also it slows down computer terribly. i checked that dma is enabled so this is not the case.

any idea what could be wrong?

---

### Post by ESPOiG on 2006-05-02
sorry to sorta change the subject Selmi

but i also have a problem when burning DVD's or CD's it slows down my computer horribly :( and this is my main comp P4 3GHz

and i have tried K3b, GnomeBaker and NeroLINUX

---

### Post by Selmi on 2006-05-02
if everuthing is slowed down its different thing,i had the same problem, solution is easy,enable dma for cdwriter
for some reason ubuntu sets dma for discs but not for cd drives

to have it set everytime you boot edit your /etc/hdparm.conf file (you must have root rights) and add somewhere this:

/dev/hdb (or whatever is your cd drive)
{
   dma=on
}

alternatively you can enable it manually running sudo hdparm -d 1 /dev/hdb (or what you need)

unfortunately this doesn't help with dvd-ram

---

