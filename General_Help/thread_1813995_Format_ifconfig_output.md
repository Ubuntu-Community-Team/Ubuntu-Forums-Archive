---
title: "Format ifconfig output"
date: 2011-07-28
forum: General Help
---

### Post by bakegoodz on 2011-07-28
I'm trying to format ifconfig output to show just the interface name and ip address. I want to show all interfaces if more than one, except loopback. I know "sed" a little bit, but I'm not smart enough with terminal text tools to get this one right. Can a CLI Guru help me out? Thanks.

---

### Post by lkjoel on 2011-07-28
> **bakegoodz said:**
> I'm trying to format ifconfig output to show just the interface name and ip address. I want to show all interfaces if more than one, except loopback. I know "sed" a little bit, but I'm not smart enough with terminal text tools to get this one right. Can a CLI Guru help me out? Thanks.
Try this:
```
for i in `ifconfig | grep "Link encap:" | awk '{print $1}'`; do echo "$i: `ifconfig $i | sed 's/inet addr:/inet addr: /' | grep "inet addr:" | awk '{print $3}'`"; done

```Example output:
```
eth1: 
eth2: 192.168.10.108
lo: 127.0.0.1
wlan0: 192.168.10.109

```If you want neater formatting, try this:
```
for i in `ifconfig | grep "Link encap:" | awk '{print $1}'`; do echo -e "$i:\t`ifconfig $i | sed 's/inet addr:/inet addr: /' | grep "inet addr:" | awk '{print $3}'`"; done

```Example output:
```
eth1:    
eth2:    192.168.10.108
lo:      127.0.0.1
wlan0:   192.168.10.109

```

---

### Post by bakegoodz on 2011-07-28
That was alot longer than expected, but it works! Thanks!
Modified to remove loopback interface

for i in `ifconfig | grep "Link encap:" | awk '{print $1}'`; do echo "$i: `ifconfig $i | sed 's/inet addr:/inet addr: /' | grep "inet addr:" | awk '{print $3}'`" | sed '/lo/d'; done

---

### Post by lkjoel on 2011-07-28
> **bakegoodz said:**
> That was alot longer than expected, but it works! Thanks!
Modified to remove loopback interface

for i in `ifconfig | grep "Link encap:" | awk '{print $1}'`; do echo "$i: `ifconfig $i | sed 's/inet addr:/inet addr: /' | grep "inet addr:" | awk '{print $3}'`" | sed '/lo/d'; done
Could you mark this thread as solved? Thread tools->Mark this thread as solved

---

### Post by bakegoodz on 2011-08-01
I was hoping for a second answer to compare. This will do. Thanks

---

