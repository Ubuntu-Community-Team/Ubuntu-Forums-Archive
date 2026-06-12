---
title: "help using dd"
date: 2009-10-12
forum: General Help
---

### Post by fouadk on 2009-10-12
hi everyone...

i am trying to use dd in order to clone one hard disk to 16 other hard disk...

what i thought of doing is create an iso image of the source hard disk and then using this image clone it to the other drives.

i am doing it this way...please correct me if im doing anything wrong


```
dd if=/dev/sdb of=/home/sam/partition.image bs=4096 conv=notrunc,noerror

```

now i have an image, then i do the following

```
]dd if=/home/sam/partition.image of=/dev/sdb bs=4096 conv=notrunc,noerror
```

is this the right way to do it ?

does anyone know of a good open-source software that can make my life easier.

please help.

thanks in advance

---

### Post by P4man on 2009-10-12
Looks okay to me, why do you think its not?
As for alternatives, [clonezilla]("http://clonezilla.org/") will let you achieve the same thing, but Im not sure how it would make your life easier.

---

### Post by fouadk on 2009-10-12
i dont think there should be a problem....im just making sure in order not to do the same thing a gazillion of time

thanks a lot again

---

### Post by renkinjutsu on 2009-10-12
looks like you used /dev/sdb which is the device name, but you didn't specify a partition, so it copied the whole device into an image

try /dev/sdb1 (if there's only one partition you'd like to copy ;))

---

### Post by P4man on 2009-10-12
> **renkinjutsu said:**
> looks like you used /dev/sdb which is the device name, but you didn't specify a partition, so it copied the whole device into an image

try /dev/sdb1 (if there's only one partition you'd like to copy ;))

if you clone only a partition, you won't get the MBR among other things. That may or may not be what he wants, but if you want to clone the entire drive as he said,  /dev/sdb is correct afaik.

---

### Post by fouadk on 2009-10-12
no this is on purpose since i need to clone the whole disk not a single partition...but thanks anyway for mentioning that

---

