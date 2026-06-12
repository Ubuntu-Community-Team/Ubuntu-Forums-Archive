---
title: "Quickly add swap space over command line"
date: 2010-03-07
forum: General Help
---

### Post by Lyuokdea on 2010-03-07
Hi All,

Working with a scientific code that uses more RAM+swap then i generally have (system has 12GB RAM + 24GB swap, but this thing is crazy)

It's kind of a one use problem, so I'm not looking to get more RAM, is there a quick way to add more swap space (not on the swap partition, because i have that set at 24GB) so that my system can use it immediately?

I don't want to drive up to the office tonight to get this fixed, so a command line setup would work best.

Thanks,

~Lyuokdea

---

### Post by flippo on 2010-03-07
I can't imagine something that uses that much swap would easily complete over night (swap is around 1000x slower than ram).

If you have enough HD space you may try a swapfile, although swap partitions are preferred.  This link contains good swap info:[http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html]("http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html")

---

### Post by Lyuokdea on 2010-03-07
thanks.... that's exactly what i need.

It should complete in an hour or two, it's basically just taking a datafile and dividing it among a billion point array. 

~Lyuokdea

---

### Post by Lyuokdea on 2010-03-07
ok...quick question about this though...

on the first command, it lists sudo dd if=/dev/zero .....

i have several different hd's on this machine, and want to add the swap space onto a specific drive. /dev/sdb7 (which is also the harddrive holding /home) how do I make sure the swap space is put on that drive?

Thanks,

~Lyuokdea

---

### Post by flippo on 2010-03-07
If your drive isn't raided then it will go on whatever drive is mounted.  If your drive is raided... I have no idea, sorry.

---

### Post by Lyuokdea on 2010-03-07
I'm confused by this....i the drive in question isn't in any specific raid mode...but there are multiple hd's on the system

~Lyuokdea

---

### Post by flippo on 2010-03-07
if you type ```
df -h
``` into a terminal you can see where all of the different drives are mounted.  put the swap file in a space on the drive you want it to be on.

Example
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              96G   58G   34G  64% /
udev                   10M  288K  9.8M   3% /dev
/dev/sda3              23G  192M   22G   1% /boot
/dev/sdb1              50G  25G    25G  50% /media/disk
shm                   1.5G     0  1.5G   0% /dev/shm

```

If I wanted my swapfile on /dev/sdb1 I would put the file on /media/disk.

---

### Post by 3rdalbum on 2010-03-07
> **Lyuokdea said:**
> ok...quick question about this though...

on the first command, it lists sudo dd if=/dev/zero .....

i have several different hd's on this machine, and want to add the swap space onto a specific drive. /dev/sdb7 (which is also the harddrive holding /home) how do I make sure the swap space is put on that drive?

Thanks,

~Lyuokdea

sudo dd if=/dev/zero of=/home/username/extraswap (and add whatever argument for how much space to use)
sudo mkswap /home/username/extraswap
sudo swapon /home/username/extraswap

...as far as I know.

---

