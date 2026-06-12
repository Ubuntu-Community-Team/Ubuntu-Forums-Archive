---
title: "Vmware server 2: configure NAT network to use external IP"
date: 2011-11-17
forum: General Help
---

### Post by aktiwers on 2011-11-17
I have a VMware server install on my server.

The server has 2 external IP's. 

I want to use one for the host OS and one for my Guest OS.

How can I do this? 

I was thinking I could configure vmnet08 to use my second external IP, but I am doing it without luck.

Can someone point me in the right direction? I want both the host and guest OS to have full internet access, with each a seperate external IP address.

Thanks!

---

### Post by salvor_hardin on 2011-11-17
Thats easy! Use bridged configuration for network! That way you assign IP address to your guest machine which is on same subnet as host.

---

### Post by aktiwers on 2011-11-18
Thanks for the reply.

Could you or someone else point me to a howto or something?

Should I create a virtual ethernet device and assign the 2. IP to it? And how do I do this?

---

### Post by aktiwers on 2011-11-18
Thanks got it working with bridge.

I just assigned IP, subnet and MAC address to the guest and had to do some internal routing on the host, which my hosting company required. Thanks!

---

