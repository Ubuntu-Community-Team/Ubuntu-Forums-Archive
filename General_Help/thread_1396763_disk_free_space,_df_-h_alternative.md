---
title: "disk free space, df -h alternative?"
date: 2010-02-02
forum: General Help
---

### Post by artheus on 2010-02-02
Hey!

I'm making a simple bash-script, where I would like to receive the total free space of a hdd partition. Without the full df -h output

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             142G  1.4G  133G   2% /
udev                 1005M  248K 1005M   1% /dev
none                 1005M     0 1005M   0% /dev/shm
none                 1005M  652K 1005M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
none                 1005M     0 1005M   0% /lib/init/rw
/dev/sdb1             1.8T   40G  1.7T   3% /data

```

I'd like it to be something like "df --used /dev/sdb1" outputs

```
40G
```

Or something like that. So I get one single value.
Is there any function for this? Or how can I achieve this?

Cheers,
Artheus

---

### Post by jamesisin on 2010-02-02
If you pipe your df output through awk you can select specific fields for return.

Maybe something like this:

```
$ df -h | grep "/dev/" | awk '{print $3}'
```

(I put grep in the pipeline because I thought you wanted only the /dev/xxxx lines.)

---

### Post by artheus on 2010-02-02
Great! Thanks!

Cheers,
Artheus

---

### Post by cjhabs on 2010-02-02
Down & dirty:
df -h | cut -c1-20,34-39

This will cut off mounts that are longer than 20 characters.
On my system:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              21G  5.1G   15G  27% /
udev                  2.9G  340K  2.9G   1% /dev
none                  2.9G  252K  2.9G   1% /dev/shm
none                  2.9G  432K  2.9G   1% /var/run
none                  2.9G     0  2.9G   0% /var/lock
none                  2.9G     0  2.9G   0% /lib/init/rw
/dev/sda6             261G  137G  111G  56% /home
192.168.33.14:/export/home
                       62G   29G   33G  48% /media/nfs

The cut filter gives:
Filesystem          Avail 
/dev/sda1             15G 
udev                 2.9G 
none                 2.9G 
none                 2.9G 
none                 2.9G 
none                 2.9G 
/dev/sda6            111G 
192.168.33.14:/expor
                      33G

---

### Post by jamesisin on 2010-02-02
> **artheus said:**
> Great! Thanks!

No problem.  I'm just learning bash so this is good practice.

Be sure to mark the thread as SOLVED in Thread Tools above.

---

