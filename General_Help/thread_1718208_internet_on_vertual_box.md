---
title: "internet on vertual box"
date: 2011-03-31
forum: General Help
---

### Post by Rakeshvijayan on 2011-03-31
Hi friends 

how the internet connection get it on virtual box.I installed ubuntu on virtual box I need an internet connection on there with out dhcp .with dhcp I can browse.I changed the settings to hostonly adapter in virtual box settings.And I changed the ip address as 192.168.1.3 ubuntu containg on virtual box .How to change the ip add of external setting means  on my original OS .

I attaching the screen shot with this thread I need to change the pointed ip to my range 192.168.1.4 this will I wish to give gate way of the ubuntu on virtual box.... 

thanks

---

### Post by Ocxic on 2011-03-31
host only networking will NOT give you Internet access as it creates a virtual network within virtualbox itself. if you want to access the net you need to use NAT or BRIDGED mode(set in virtualbox settings for the VM). NAT will put you computer behind a virtual router of sorts. BRIDGED will connect your virtual machine directly to your network just like a normal computer, the you just need to configure your guest OS's network settings that you want to use.

---

### Post by Rakeshvijayan on 2011-03-31
> **Ocxic said:**
> host only networking will NOT give you Internet access as it creates a virtual network within virtualbox itself. if you want to access the net you need to use NAT or BRIDGED mode(set in virtualbox settings for the VM). NAT will put you computer behind a virtual router of sorts. BRIDGED will connect your virtual machine directly to your network just like a normal computer, the you just need to configure your guest OS's network settings that you want to use.


ok I changed it what should do next?..on gust os what settings is needed on network configuration means dhcp ,manul,localy link ...

---

### Post by Ocxic on 2011-03-31
that depends on you network. If your using bridged mode then just make the guest settings the same as your host computer. if you set a static address just be sure it's not in use on your network.

SideNote: ignore the vmnet0 connection on your host OS, that is only used with host only and internal networking options.

---

