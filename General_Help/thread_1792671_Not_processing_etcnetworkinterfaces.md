---
title: "Not processing /etc/network/interfaces"
date: 2011-06-28
forum: General Help
---

### Post by sropensrc on 2011-06-28
Hi,

I'm running 10.04 lucid and seems on startup it's not processing 

/etc/network/interfaces, ifconfig just shows "lo inet addr:127.0.0.1 ...".

Running "sudo /etc/init.d/networking restart" doesn't work.  To get the network 

started I'd have to run "sudo ifconfig eth0 IP newmask 255.255.0.0 up"  then I have 

to add route.

Anybody know why it's not reading the /etc/network/interfaces file?

Thank You

---

### Post by tcsmith1978 on 2011-06-28
Hi,

Can you post your /etc/network/interfaces here?

Thanks,

Tim

---

### Post by sropensrc on 2011-06-28
Here's the content of my interfaces file.  Thanks

# The loopback network interface
auto lo
iface lo inet loopback

auth eth0
iface eth0 inet static
        address 10.1.90.65
        netmask 255.255.0.0
        gateway 10.1.1.249

---

### Post by sropensrc on 2011-06-28
After looking at the interfaces more carefully, I see that I have "auth eth0" instead of "auto eth0".  Thanks for your help.

---

### Post by tcsmith1978 on 2011-06-28
I didn't really help! If that worked tho - can you mark this thread as solved? Thanks!

Tim

---

