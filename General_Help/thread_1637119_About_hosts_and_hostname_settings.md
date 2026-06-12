---
title: "About hosts and hostname settings"
date: 2010-12-04
forum: General Help
---

### Post by satimis on 2010-12-04
Hi folks,

Ubuntu 10.10 64 bit


I need to set /etc/hostname and /etc/hosts so that on running;

$ hostname```

ub1004

```

$ hostname -a```

ub1004

```


I set them as;

cat /etc/hostname```

ub1004

```

cat /etc/hosts```

127.0.0.1	localhost.localdomain
123.123.123.123	ub1004.domain.com	ub1004

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

After reboot:

cat /etc/hostname```

ub1004

```

$ cat /etc/hosts```

127.0.0.1	ub1004	localhost.localdomain	localhost
::1	ub1004	localhost6.localdomain6	localhost6
#127.0.1.1	ub1004
123.123.123.123	ub1004.domain.com	ub1004

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```


On running

$ hostname```

ub1004

```

$ hostname -a```

localhost.localdomain localhost localhost6.localdomain6 localhost6 ub1004 ub1004.domain.com

```

Please advice.

TIA


B.R.
satimis

---

### Post by dcstar on 2010-12-04
> **satimis said:**
> Hi folks,

Ubuntu 10.10 64 bit


I need to set /etc/hostname and /etc/hosts so that on running;

$ hostname```

ub1004

```

$ hostname -a```

ub1004

```
.........

Well you can't, they are the way they are because the system needs them that way.

hostname -a displays all the alias names for a host, and it works exactly how it is supposed to. Do not use it if you you don't want it to do what it is supposed to do.

---

### Post by satimis on 2010-12-04
> **dcstar said:**
> Well you can't, they are the way they are because the system needs them that way.

hostname -a displays all the alias names for a host, and it works exactly how it is supposed to. Do not use it if you you don't want it to do what it is supposed to do.

Hi,

OK.  Thanks for your advice.

But after reboot why /etc/hosts
changes to:```

127.0.0.1	ub1004	localhost.localdomain	localhost
::1	ub1004	localhost6.localdomain6	localhost6
#127.0.1.1	ub1004
123.123.123.123	ub1004.domain.com	ub1004

```


B.R.
satimis

---

