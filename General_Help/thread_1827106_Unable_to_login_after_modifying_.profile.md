---
title: "Unable to login after modifying .profile"
date: 2011-08-17
forum: General Help
---

### Post by alan89 on 2011-08-17
Hi Guys,

Changed environmental variable PATH in Ubuntu after installing  Android SDK. Now I am unable to login! Think I changed the wrong thing. 

Can I undo my change? Any help please?

Thanks.

---

### Post by lmarmisa on 2011-08-17
Boot into an Ubuntu Live CD / USB, open a terminal and type this command:

```

sudo fdisk -l

```

Try to identify the partition where your file .profile is stored (I will suppose this is /dev/sda1, but change it if necessary).

Then mount this partition:

```

sudo mount /dev/sda1 /mnt

```

Finally edit your file .profile:

```

sudo gedit /mnt/home/yourusername/.profile

```

---

### Post by alan89 on 2011-08-17
> **lmarmisa said:**
> Boot into an Ubuntu Live CD / USB, open a terminal and type this command:

```

sudo fdisk -l

```

Try to identify the partition where your file .profile is stored (I will suppose this is /dev/sda1, but change it if necessary).

Then mount this partition:

```

sudo mount /dev/sda1 /mnt

```

Finally edit your file .profile:

```

sudo gedit /mnt/home/yourusername/.profile

```


That worked perfect! Thank You!!!:KS

---

### Post by lmarmisa on 2011-08-17
Great!!!. :D

Please, mark the thread as SOLVED (look at Thread Tools link).

---

