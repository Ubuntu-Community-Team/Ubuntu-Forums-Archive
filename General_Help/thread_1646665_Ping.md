---
title: "Ping"
date: 2010-12-16
forum: General Help
---

### Post by sureshk89 on 2010-12-16
Hi
I am planning for remote desktop from windows pc.
I have 1 linux and 6 windows pc.
I able ping all pc's from my linux,I am not able to ping my linux pc from any windows system.
I tried disabling firewall
Thanks and Regards
Suresh

---

### Post by pellgarlic on 2010-12-17
are you sure you have no firewall on the linux pc? open a terminal and type:

```
# sudo iptables -L
```

the output should look like this if there is no active firewall:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

if there is anything in there, it might be required, but to test, you could try:

```
sudo iptables --flush
```

to clear it out, and test pinging. 


if this still doesn't work, i would reckon it's something to do with your network setup, rather than the linux pc... e.g. - is the ip you've given the linux pc within the subnet mask used by the windows pcs?

---

### Post by mendhak on 2010-12-20
> **sureshk89 said:**
> Hi
I am planning for remote desktop from windows pc.
I have 1 linux and 6 windows pc.
I able ping all pc's from my linux,I am not able to ping my linux pc from any windows system.
I tried disabling firewall
Thanks and Regards
Suresh
Are you pinging the linux box by name or IP address?

---

