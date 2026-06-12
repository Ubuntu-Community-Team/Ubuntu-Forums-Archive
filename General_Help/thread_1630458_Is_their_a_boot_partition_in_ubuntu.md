---
title: "Is their a boot partition in ubuntu?"
date: 2010-11-25
forum: General Help
---

### Post by a quarter past seven on 2010-11-25
is their a boot partiton that need to be kept seperate in ubuntu?

[ATTACH]176537[/ATTACH]

those are my partitons in the pic above am i okay to merge them all into the dev/sda2 or is it like windows and i need to keep a small section back for the boot?

---

### Post by wojox on 2010-11-25
You can keep it separate if you want or you can just install it with /. What are you trying to do?

---

### Post by a quarter past seven on 2010-11-25
> **wojox said:**
> You can keep it separate if you want or you can just install it with /. What are you trying to do?

im trying to just get to one big partiton turning dev/sda2 into my only partiton, but i cant make a live cd for a while so im just gona merge the rest of them in the mean time, i just wasent sure which part was responsible for booting and stuff or wether the booting thing is kept on the same partiton you keep ubuntu on, so wasent sure wether its safe to resize them all

---

### Post by kanishkdudeja on 2010-11-25
sda1 is your boot partition..

you can merge all your partitions..its not compulsory that boot partition has to be separate..

but while merging moving partitions..

please backup your data as it might get lost..

n you can merge using gparted from the live cd..

---

### Post by a quarter past seven on 2010-11-25
> **kanishkdudeja said:**
> sda1 is your boot partition..

you can merge all your partitions..its not compulsory that boot partition has to be separate..

but while merging moving partitions..

please backup your data as it might get lost..

n you can merge using gparted from the live cd..


ok cheers for answering, an yeh ill back up i learnt the hard way about how important it is to back up....

---

### Post by kanishkdudeja on 2010-11-25
no problems..

---

