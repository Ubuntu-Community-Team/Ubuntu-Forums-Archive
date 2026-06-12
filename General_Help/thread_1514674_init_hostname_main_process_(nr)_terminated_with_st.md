---
title: "init: hostname main process (nr) terminated with status 1"
date: 2010-06-21
forum: General Help
---

### Post by moment92 on 2010-06-21
After updating to Ubuntu 10.04 LTS, a message started appearing after the grub boot screen:
init: hostname main process (nr) terminated with status 1

Really bad experiences with the new Ubuntu...

---

### Post by moment92 on 2010-06-21
When I think about it, it is probably connected to the fact that I changed my computer name by modifying "hostname" and "hosts" files. I changed it 2 days ago, but probably I just didn't notice the error message before.

Any suggestions on how to fix the problem?

---

### Post by Iowan on 2010-06-21
[This]("http://www.psychocats.net/ubuntu/fixsudo#recoverymode") article *might*  help - especially the part about booting into recovery mode. From there, you should be able to check/correct the */etc/hosts* and */etc/hostname* files.

---

### Post by moment92 on 2010-06-22
The problem is, that I am not sure what those files should look like.
My files contain these lines:

hostname:
```
my-computer
```

hosts:
```

127.0.0.1    my-computer    localhost.localdomain    localhost

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

How should I fix them?

---

### Post by Claus7 on 2010-10-13
Hello,

> **Iowan said:**
> [This]("http://www.psychocats.net/ubuntu/fixsudo#recoverymode") article *might*  help - especially the part about booting into recovery mode. From there, you should be able to check/correct the */etc/hosts* and */etc/hostname* files.

this helped me as well, as in ubu 10.10 when I decided to change the hostname this message appeared.

I had to log out, enter recovery console and from there just typing:
sudo vim /etc/hosts
sudo vim /etc/hostname

I changed _all_ the strings that had to do with the name of my computer. Rebooted and the message disappeared.

Thanks,
Regards!

---

### Post by pedroazenham on 2010-12-09
> **moment92 said:**
> The problem is, that I am not sure what those files should look like.
My files contain these lines:

hostname:
```
my-computer
```hosts:
```

127.0.0.1    my-computer    localhost.localdomain    localhost

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```How should I fix them?


Hi, 
The problem is that you are using invalid characters (like _ -) in your host name.
Edit the /etc/hostname file and change it.
This will fix that error.

---

