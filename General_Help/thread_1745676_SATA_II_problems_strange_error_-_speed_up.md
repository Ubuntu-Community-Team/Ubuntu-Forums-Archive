---
title: "SATA II problems/ strange error - speed up?"
date: 2011-05-01
forum: General Help
---

### Post by listerdl on 2011-05-01
I keep getting this error in my log viewer every 2 seconds:

```
ata4: limiting SATA link speed to 1.5 Gbps
```

I have a dual boot SSD and I have run many SMART tests in windows and linux, (using smartmon tools and the disk utility) and the reports are all 100% healthy.....

My research shows that this error represents one of the following:

1. Problem with SATA controller
2. Changing BIOS to allow SATA
3. Changing SATA mode to PATA or AHCI
4. Replacing the SATA cable
[COLOR="Blue"]5. Allowing the SSD to run at SATA II speeds, i.e. 3 Gbps

- Does anyone know how to try number 5, i.e. allowing the SSD to run at SATA II speeds?[/COLOR]

I am lost here and this problem has caused my machine to crash twice when watching a movie in linux/ ubuntu.

(It is worth noting that the crashes have only occurred in linux and I have never had an issue in windows, so it does seem to be a linux setting somewhere, hence why I think it is a "allowing SATA II to run at correct speeds issue")

THANKS FOR ALL REPLIES!!

---

### Post by sdowney717 on 2011-05-01
I know drives have a jumper hat tells the drives either sata or sata2

---

### Post by listerdl on 2011-05-01
> **sdowney717 said:**
> I know drives have a jumper hat tells the drives either sata or sata2

Thanks - can you expand on that? Not sure how to check for that - thanks

---

### Post by sdowney717 on 2011-05-01
On my sata drives, a black electrical jumper  exists which connects various pins to tell the drive to run in sata compatibility or sata 2 mode.

I dont have solid state drives, so I dont know if they do have a jumper.

---

### Post by listerdl on 2011-05-01
thanks - can this be checked using a command?

---

