---
title: "vmware network settings"
date: 2011-09-01
forum: General Help
---

### Post by HarriU11-04 on 2011-09-01
Hello

I have a Windows host with a vmware Ubuntu server virtual machine  running on it. The two machines can see each other (Ping, etc.). In  firefox, if the connection settings point to the vm, the browser can  access the Internet, no problem. The VM talks to the physical machine  via NAT virtual adapter thingy (ie, default settings)

I want to restrict/control the http traffic on the Windows host so it can only access the Internet via the VM.

Any ideas as to how I can achieve this?

---

### Post by haqking on 2011-09-01
> **HarriU11-04 said:**
> Hello

I have a Windows host with a vmware Ubuntu server virtual machine  running on it. The two machines can see each other (Ping, etc.). In  firefox, if the connection settings point to the vm, the browser can  access the Internet, no problem. The VM talks to the physical machine  via NAT virtual adapter thingy (ie, default settings)

I want to restrict/control the http traffic on the Windows host so it can only access the Internet via the VM.

Any ideas as to how I can achieve this?

you mean you want your VM as gateway ?

Your VM accesses the internet through your host anyways, so you would be routing internet traffic through the VM to route back your own network interface on your host, whats the point in that ?

---

### Post by HarriU11-04 on 2011-09-01
> **haqking said:**
> 
Your VM accesses the internet through your host anyways, so you would be routing internet traffic through the VM to route back your own network interface on your host, whats the point in that ?
I know that, however the VM is acting as a web filter (Dansguardian + squid + iptables rules). 
What would be the best way of achieving this so that I can keep some Windows programs? E.g. Metatrader functionality is not all there in wine. I've tried a linux host and vmware Windows guest, but Ubuntu desktop takes too much resources. I know there are DansG(linux) virtual appliances in the marketplace, but if I download one of them I cannot work out how to prevent a Windows user just by-passing the virtual webfilter in the browser proxy settings. What would be the point of that? I should mention that everything needs to run off 1 physical box - a laptop.

Suggestions/Ideas/Directions to point me to?

---

### Post by haqking on 2011-09-01
> **HarriU11-04 said:**
> I know that, however the VM is acting as a web filter (Dansguardian + squid + iptables rules). 
What would be the best way of achieving this so that I can keep some Windows programs? E.g. Metatrader functionality is not all there in wine. I've tried a linux host and vmware Windows guest, but Ubuntu desktop takes too much resources. I know there are DansG(linux) virtual appliances in the marketplace, but if I download one of them I cannot work out how to prevent a Windows user just by-passing the virtual webfilter in the browser proxy settings. What would be the point of that? I should mention that everything needs to run off 1 physical box - a laptop.

Suggestions/Ideas/Directions to point me to?


ok so yeah in that case then make the VM your web proxy....i think ;-)

---

