---
title: "resolv.conf issue"
date: 2006-03-19
forum: General Help
---

### Post by crypticstatic on 2006-03-19
Hello all,

I have a strange problem. I was experiencing problems browing the internet  and long story short I found that in the resolv.conf file the first host was pointing to my router for DNS resolution. 

I removed that entry and SAVED the file while I was root but yet, every time I reboot the system the entry I deleted is right back in the resolv.conf file and I have to edit it again!

Am I missing something here? Why does the router IP address keep getting written back into my resolv.conf file?

I'm usung Kubuntu 5.10 and I have a linksys wrt54g wireless router. I have this machine connected directly to my router.

Any help would be greatly appreciated.

---

### Post by Zelut on 2006-03-19
I found, on my system, that the DHCP tries to auto-detect the settings and sometimes will just write what it find (the router) as the DNS.  This will work in some cases, but others wont actually get outside to the right DNS.

What I did was edit my /etc/dhcp3/dhclient.conf and un-comment the line "prepend domain-name-servers XX.XX.XX.XX" (XX representing your actual DNS.)

This will auto-prepend your resolv.conf with the correct DNS entry anytime you reboot, restart networking, etc.

I hope this helps.

---

### Post by crypticstatic on 2006-03-19
That has seemed to fix the problem! Thank you.

What a bizare problem. I've been administering Linux systems for some time now and this is the first time I've encountered this problem, on my own system no less!

I appreciate the help.

---

### Post by AndreAPL on 2006-03-20
hi there. i had the same issue. Thanks, it worked :)

---

### Post by sherlock-holmes on 2006-03-21
[QUOTE=kuyaedz]I found, on my system, that the DHCP tries to auto-detect the settings and sometimes will just write what it find (the router) as the DNS.  This will work in some cases, but others wont actually get outside to the right DNS.

What I did was edit my /etc/dhcp3/dhclient.conf and un-comment the line "prepend domain-name-servers XX.XX.XX.XX" (XX representing your actual DNS.)

This will auto-prepend your resolv.conf with the correct DNS entry anytime you reboot, restart networking, etc.

I hope this helps.[/QUOTE]

i cant connect either...what if i dont know the DNS? the router gives me that automatically.. i never had to thnk about this before sometime...I did a dist-upgrade and noting seems to work with the wireless... using XP now...

its a managed home network....:cry:

---

### Post by Zelut on 2006-03-21
You should be able to find your DNS listed on your router config.  I never had problems with mine until we got a new ISP, and then I had to manually set the DNS as well..

---

