---
title: "syslog getting filled with &quot;...IN=br0 OUT=br0 PHYSIN=eth0 PHYSOUT=tap0...&quot; lines"
date: 2011-04-01
forum: General Help
---

### Post by KhurramF on 2011-04-01
On Ubuntu 9.10, I have bridged eth0 and tap0 and have OpenVPN using it. The bridge and VPN connections are working okay. But syslog file shows the following lines:

```
Apr  1 18:22:25 <hostname> kernel: [193828.792411] IN=br0 OUT=br0 PHYSIN=eth0 PHYSOUT=tap0 SRC=x.x.x.x DST=239.255.255.250 LEN=331 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=311 
Apr  1 18:22:25 <hostname> kernel: [193828.792821] IN=br0 OUT=br0 PHYSIN=eth0 PHYSOUT=tap0 SRC=x.x.x.x DST=239.255.255.250 LEN=340 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=320 
Apr  1 18:22:25 <hostname> kernel: [193828.793555] IN=br0 OUT=br0 PHYSIN=eth0 PHYSOUT=tap0 SRC=x.x.x.x DST=239.255.255.250 LEN=403 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=383 
Apr  1 18:22:25 <hostname> kernel: [193828.794252] IN=br0 OUT=br0 PHYSIN=eth0 PHYSOUT=tap0 SRC=x.x.x.x DST=239.255.255.250 LEN=395 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=375 
```

These lines keep on appearing almost continuously. As a result, the syslog file gets huge very fast. I have no idea what is generating these lines or how to get rid of them in the log.

Can someone please help me out here?

Thanks.

---

### Post by bodhi.zazen on 2011-04-01
Do you have logging enabled in iptables or ufw ? If so, turn it off or set it to a lower threshold.

---

### Post by KhurramF on 2011-04-01
> **bodhi.zazen said:**
> Do you have logging enabled in iptables or ufw ? If so, turn it off or set it to a lower threshold.
That's it. It was a logging rule in iptables for the forward chain. Thanks so much.

Btw, what is ufw?

---

### Post by bodhi.zazen on 2011-04-01
Uncomplicated FireWall

It is a command line configuration tool for iptables. The graphical front end is gufw.

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by KhurramF on 2011-04-01
> **bodhi.zazen said:**
> Uncomplicated FireWall

It is a command line configuration tool for iptables. The graphical front end is gufw.

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Thanks, I didn't know that.

---

