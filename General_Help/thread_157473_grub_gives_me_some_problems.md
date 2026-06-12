---
title: "grub gives me some problems"
date: 2006-04-09
forum: General Help
---

### Post by IGNIZ on 2006-04-09
at startup grub hangs for 2 minutes at 100% of cpu using, it stops after booting the kernel, it says he is booting the kernel and hangs.
a strange thing i noticed is that grub says my fs is ext2, while it's ext3, maybe is this the problem? and how can i solve it?

thanks

---

### Post by IGNIZ on 2006-04-09
i made a verbose boot and it loops on something like this:

/dev/ide/host0/bus0/target0/lun0

dma: dma timeout error

it loops for 2 minutes, then it boot normally

---

### Post by IGNIZ on 2006-04-09
hem ](*,)

i turned dma on and now there is no problem :rolleyes:

if anyone got same problem, type

```
hdparm -d1 /dev/hda
```

if on primary hd, hdb secondary etc

---

### Post by IGNIZ on 2006-04-09
oh man, this doesn't work anymore after a shutdown, how can i make this setting permanent? i think it should be related to bios...

---

### Post by IGNIZ on 2006-04-09
mmm... and enabling it by default recompiling kernel? someone knowns?

---

### Post by IGNIZ on 2006-04-10
i'm talking alone ;_;

---

