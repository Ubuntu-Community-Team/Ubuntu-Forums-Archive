---
title: "Setting up a router"
date: 2010-03-05
forum: General Help
---

### Post by satty8610 on 2010-03-05
I have to configure a virtual machine A as a router that routes traffic between 2 other virtual machines, B and C. 
Though there are many pages on the internet that deal with setting up a router , I couldn't find any that tells about what configuration changes need to be made on the VMs B and C.
Can someone post exactly, what steps need to be taken(sequence of commands) ?

Also, I tried out this thing that B and C were set on different LANs (through virtual network settings) , so that they could not ping each other. After running the following command on each of the machines, the 2 machines were able to ping each other ```
ip route add default via ####(default gateway address of machine B/C)
```
I never configured A as a router, and still B and C could ping each other, despite being on different LANs!!!
What the heck is this? 

Answers to both my questions are welcome.

---

### Post by gmargo on 2010-03-05
You should specify what VM software you are using, as well as what host & guest OSs. And network configurations.

---

### Post by satty8610 on 2010-03-05
> **gmargo said:**
> You should specify what VM software you are using, as well as what host & guest OSs. And network configurations.

i am using vmware workstation.
host os: ubuntu desktop 9.10
guest os(es): ubuntu server 9.10
network configs: host only network settings. B has network interface vmnet1, C has vmnet2. A has 2 network interfaces: vmnet1 and vmnet2.

---

