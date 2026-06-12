---
title: "Setting a variable in /proc space"
date: 2006-06-29
forum: General Help
---

### Post by v4169sgr on 2006-06-29
I need to support an ancient PXE client firmware, but am having difficulties making the necessary adjustments.

sudo echo 1 > /proc/sys/net/ipv4/ip_no_pmtu_disc
bash: /proc/sys/net/ipv4/ip_no_pmtu_disc: Permission denied

ls -lsart /proc/sys/net/ipv4/ip_no_pmtu_disc
0 -rw-r--r-- 1 root root 0 2006-06-29 22:24 /proc/sys/net/ipv4/ip_no_pmtu_disc

Setting 666 permissions gives:

echo 1 > /proc/sys/net/ipv4/ip_no_pmtu_disc
bash: echo: write error: Operation not permitted

How therefore do I set 1 to this variable?

---

### Post by hayalci on 2006-06-29
That may be a read-only variable, or there may be a kernel module to load before you can change the variable.

---

### Post by v4169sgr on 2006-06-29
It's not read-only; I've seen reference to it being changed. Could you be a little more specific about the kernel module bit?

Thanks!

---

### Post by mlind on 2006-06-29
your command is wrong

```

sh -c "sudo echo 1 > /proc/sys/net/ipv4/ip_no_pmtu_disc"

```

or

```

echo 1 | sudo tee /proc/sys/net/ipv4/ip_no_pmtu_disc

```

to permanenty set this value see 
```

man sysctl

```

and /etc/sysctl.conf

---

### Post by thasheep on 2006-06-29
The permission denied is because sudo can't handle redirecting output with root previleges. Not sure if that makes much sense but try this instead

sudo -i   # enter a root shell (like su)
echo 1 > /proc/sys/net/ipv4/ip_no_pmtu_disc
exit

(edit)mlind beat me to it - different way to solve the same problem

---

### Post by v4169sgr on 2006-06-29
Thank you very much all - this is effective.

---

