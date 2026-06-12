---
title: "File system not mounting correctly"
date: 2010-06-29
forum: General Help
---

### Post by sunnyengineeer on 2010-06-29
Hello,
         I had Ubuntu 10.04 only..untill I installed Linux Mint on one drive which was created by WIndows in NTFS format....

So that I have tripple boot PC...:)
But whenever I start in Ubuntu it gives an error message :-

" Mounting of ACTION drive error,Press "S" to skip mounting it,Press "M" for manual recovery"

Each time I've to press "S" to overcome this...
Can I sort out this problem permanently ..
The drive name was ACTION..& was at sda5..acc to Linux..& Im using NTFS-COnfig to automount my drives...

Thnx
SUnny

---

### Post by sunnyengineeer on 2010-06-30
Somebody plz help me out of this....

---

### Post by dabl on 2010-06-30
```
cat /etc/fstab
```

and post the output here, please.

---

### Post by qsuc on 2010-07-08
> **dabl said:**
> ```
cat /etc/fstab
```

and post the output here, please.

```
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0


```

Same issue. The error screen restarts the machine so quickly, I don't know a way to get into a terminal and run fstab from the filesystem itself. I'm on a live usb to post this.

---

