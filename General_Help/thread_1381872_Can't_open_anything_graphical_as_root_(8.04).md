---
title: "Can't open anything graphical as root (8.04)"
date: 2010-01-15
forum: General Help
---

### Post by Famicube64 on 2010-01-15
Whenever I'm connected a network, anything graphical fails to open with gksu, or sudo. As soon as I disable networking everything works as it should. There're no CDs in my DVD drives. What could be happening? This is a fresh install, by the way.

---

### Post by Famicube64 on 2010-01-15
Bump.

---

### Post by d3v1150m471c on 2010-01-15
Absolutely nothing with a gui will work? What is it you are trying to open and why? Let me know and I can probably help you out, if not another brosef on the forum.

---

### Post by Famicube64 on 2010-01-15
Anything thing that opens with a graphical interface won't open as root. For example, gksudo nautilus. It opens after about 5 minutes, but doesn't respond. I can open the same thing as normal user and it works fine. I can also open it as root when I disable networking. I read somewhere about a change to the host file would fix it, but that was just what I gleaned from the Google search snippet. The actual site was down.

---

### Post by Famicube64 on 2010-01-15
Bump.

---

### Post by Famicube64 on 2010-01-15
Bump.

---

### Post by doas777 on 2010-01-15
post the output of 
```
dmesg | tail
```

and try running 'gksu nautilus' from a terminal and post any messages that follow.

---

### Post by Famicube64 on 2010-01-15
```
tyler@ubuntu:~$ dmesg | tail
[ 6295.127892] ACPI: Unable to turn cooling device [f7c44f18] 'on'
[ 6301.122106] ACPI: Unable to turn cooling device [f7c44f18] 'on'
[ 6307.116102] ACPI: Unable to turn cooling device [f7c44f18] 'on'
[ 6313.110214] ACPI: Unable to turn cooling device [f7c44f18] 'on'
[ 6319.104329] ACPI: Unable to turn cooling device [f7c44f18] 'on'
[ 6325.098503] ACPI: Unable to turn cooling device [f7c44f18] 'on'
[ 6331.092636] ACPI: Unable to turn cooling device [f7c44f18] 'on'
[ 6337.086719] ACPI: Unable to turn cooling device [f7c44f18] 'on'
[ 6343.080871] ACPI: Unable to turn cooling device [f7c44f18] 'on'
[ 6349.074970] ACPI: Unable to turn cooling device [f7c44f18] 'on'
tyler@ubuntu:~$ 
``````
tyler@ubuntu:~$ gksudo nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized
```After gksudo nautilus it just sits there. Doesn't even ask for a password. If I disable networking, it works fine.

Edit: I can sudo su to a root terminal from a regular terminal, but if I open a root terminal from the gnome menu it just asks for my password. Never opens.

---

### Post by Famicube64 on 2010-01-15
Bump.

---

### Post by d3v1150m471c on 2010-01-15
that's the weirdest thing i've ever heard of...

---

### Post by Famicube64 on 2010-01-15
Pretty much. D:

---

### Post by louieb on 2010-01-15
post the content of 
/etc/hosts
and
/etc/hostname

btw: turn off your bump machine;)

---

### Post by Famicube64 on 2010-01-15
Hosts
```

127.0.0.1 localhost
127.0.1.1 ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Hostname

```
ubuntu
```

---

### Post by doas777 on 2010-01-15
> **louieb said:**
> post the content of 
/etc/hosts
and
/etc/hostname

btw: turn off your bump machine;)

I thought the same thing, but that issue usually only affects sudo, leaving gksu working (and thank goodness for that since it's the only way to fix sudo easily).

I'm scratchin my head too.

Op, standard wisdom is to wait 24 hours before bumping. sry to lecture.

---

### Post by louieb on 2010-01-15
/etc/hosts and /etc/hostname looks fine - not the problem.

Out of ideas - so heres a bump:D

---

### Post by dcstar on 2010-01-16
> **Famicube64 said:**
> Whenever I'm connected a network, anything graphical fails to open with gksu, or sudo. As soon as I disable networking everything works as it should. There're no CDs in my DVD drives. What could be happening? This is a fresh install, by the way.

Are you using Network Manager?

---

### Post by d3v1150m471c on 2010-01-16
Is it possible that the monolithic kernel is becoming confused or malfunctioning because he's trying to pull the same data from its shared pool? IE Is this user's computer not allowing him to access superuser resources because his network is also pulling from that stream of data? I'm not to savvy with things that advanced so perhaps someone who knows more about this kind of thing indepth would have some insight.

---

### Post by Famicube64 on 2010-01-16
> **dcstar said:**
> Are you using Network Manager?Yes, I am.

---

