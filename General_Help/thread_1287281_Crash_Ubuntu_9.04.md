---
title: "Crash Ubuntu 9.04"
date: 2009-10-10
forum: General Help
---

### Post by nipunreddevil on 2009-10-10
Recently i have been experiencing crashes in Ubuntu 9.04.Does that have to do anything with my hard disk almost filled.And these crashes are really bad,force quit also doesn't work

---

### Post by ZaHACKieL on 2009-10-10
Have you noticed a pattern followed by the crashes? or they just happen randomly?

ZL

---

### Post by nipunreddevil on 2009-10-10
They are quite random and they are really bad..and some lines appear on the top of the screen before it actually freezes

---

### Post by sloggerkhan on 2009-10-10
have you checked if your disk is full? (df command may be helpful)
Though if lines appear in the screen, I'd tend to think graphics or memory issues more than hd issues.

---

### Post by nipunreddevil on 2009-10-10
This is what df command gave:[HTML]/host/ubuntu/disks/root.disk
                      16876388  15888744    130352 100% /
tmpfs                  1418240         0   1418240   0% /lib/init/rw
varrun                 1418240       332   1417908   1% /var/run
varlock                1418240         0   1418240   0% /var/lock
udev                   1418240       156   1418084   1% /dev
tmpfs                  1418240       224   1418016   1% /dev/shm
/dev/sda2            236476412 182164828  54311584  78% /host
lrm                    1418240      2192   1416048   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sda1              1535996    147376   1388620  10% /media/TOSHIBA SYSTEM VOLUME
/dev/sda3              6184956   5581096    603860  91% /media/HDDRECOVERY
[/HTML]

So not sure about the reason.Also if i turn on compiz effects and play videos in totem,system crashes.
I have ATI Radeon 3100 grpahics card.

---

### Post by sloggerkhan on 2009-10-10
> **nipunreddevil said:**
> This is what df command gave:[HTML]/host/ubuntu/disks/root.disk
                      16876388  15888744    130352 100% /
tmpfs                  1418240         0   1418240   0% /lib/init/rw
varrun                 1418240       332   1417908   1% /var/run
varlock                1418240         0   1418240   0% /var/lock
udev                   1418240       156   1418084   1% /dev
tmpfs                  1418240       224   1418016   1% /dev/shm
/dev/sda2            236476412 182164828  54311584  78% /host
lrm                    1418240      2192   1416048   1% /lib/modules/2.6.28-15-generic/volatile
/dev/sda1              1535996    147376   1388620  10% /media/TOSHIBA SYSTEM VOLUME
/dev/sda3              6184956   5581096    603860  91% /media/HDDRECOVERY
[/HTML]

So not sure about the reason.Also if i turn on compiz effects and play videos in totem,system crashes.
I have ATI Radeon 3100 grpahics card.

```
/host/ubuntu/disks/root.disk
                      16876388  15888744    130352 100% / 
```

means your root partition is pretty much 100% full, which can cause problems.

Though /host/ubuntu/disks/root.disk is odd... are you running in a vm or with wubi?

---

### Post by nipunreddevil on 2009-10-10
I am running it with wubi

---

### Post by sloggerkhan on 2009-10-11
It looks like you should grow your root partition to me, but not an expert on that.

---

