---
title: "x forwarding not working when ipv6 disabled"
date: 2010-12-20
forum: General Help
---

### Post by PrSdNt on 2010-12-20
Hi,

Got Ubuntu Server 10.10 installed as a virtual machine (vmware). When i forward X through SSH (putty) i can start xeyes, xcalc,etc. 

Now when i disable ipv6 putty can't set the display variable and i get "Error: can't open display". I haven't changed anything in putty or win 7 (the host system). 

I disable ipv6 by putting these lines in /etc/sysctl.conf

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

Has anyone have any idea why this is happening? Thanks

---

### Post by TheGrave on 2011-04-30
Same issue here. Did you manage to resolve it?

---

### Post by Ubscenee on 2011-05-02
A workaround is appending

```

AddressFamily inet

```in the remote host /etc/ssh/sshd_config file, then 

```

sudo service ssh restart

```Had the same issue and now is working!

---

### Post by bdw on 2011-05-03
> **Ubscenee said:**
> A workaround is appending

```

AddressFamily inet

```in the remote host /etc/ssh/sshd_config file, then 

```

sudo service ssh restart

```Had the same issue and now is working!
Awesome!  Thanks for sharing this! :D

Hopefully a work around will be implemented so that when IPv6 is disabled it won't disable running X apps via ssh.

---

### Post by Jive Turkey on 2011-05-03
> **Ubscenee said:**
> A workaround is appending

```

AddressFamily inet

```in the remote host /etc/ssh/sshd_config file, then 

```

sudo service ssh restart

```Had the same issue and now is working!

Wow, I have tried everything and the kitchen sink to get this fixed and here it is!

---

### Post by Yo Nas on 2011-08-25
Thnx Ubscenee!:)

---

