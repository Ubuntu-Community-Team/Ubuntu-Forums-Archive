---
title: "Unable to connect Internet"
date: 2010-08-07
forum: General Help
---

### Post by satimis on 2010-08-07
Hi folks,

host - Ubuntu 1004 64 bit
new vm - Ubuntu 1004 64 bit (cloned on another VM)

After creating this new vm it starts/works

Edit /etc/network/interface to change the IP address
Edit /etc/hosts and /etc/hostname to change hostname

reboot vm

$ hostname
showing the correct/new hostname

$ sudo ifconfig
showing the correct IP


But vm can't ping host nor Internet.  Nor host can ping the new vm.

This is NOT my first time cloning vm.  There are many cloned vm running on this VBox.  I have spent more than an hour unable to solve the problem.  Please help.

/etc/resolv.conf 
is correct showing the DNS IP of ISP

B.R.
satimis

---

### Post by corrytonapple on 2010-08-07
Have you reset the modem box or router or both?

---

### Post by rubylaser on 2010-08-07
Just a few questions:  Is the network bridged or NAT'd? Can you ping the VM host? Can you ping the gateway?  Do DNS names resolve properly on the LAN?

---

### Post by satimis on 2010-08-07
> **corrytonapple said:**
> Have you reset the modem box or router or both?

Hi,

The PC is connected to the router.  I haven't made any change.

B.R.
satimis

---

### Post by satimis on 2010-08-07
> **rubylaser said:**
> Just a few questions:  Is the network bridged or NAT'd? Can you ping the VM host? Can you ping the gateway?  Do DNS names resolve properly on the LAN?

Hi,

It is a bridged network

VM can't ping the host nor gateway

IIRC after creating this new vm it can connect Internet and download packages on repo.  After changing its IP address and hostname it can't connect Internet anymore.

What I discovered on /etc/hosts I made following changes```

27.0.0.1        localhost
127.0.1.1       hostname
IP address      hostname.domain.com  hostname
....

```

After reboot it becomes```

27.0.0.1        localhost.localdomain  localhost
127.0.1.1       hostname
IP address      hostname.domain.com  hostname
....

```

I haven't made any change on /etc/resolv.conf.  The file is the same as on the original vm which is still working

B.R.
satimis

---

### Post by satimis on 2010-08-07
Hi folks,

I found something strange here.

The browser, Firefox, can connect Internet.  On terminal it can ping Internet but can't ping host/gateway

B.R.
satimis

---

