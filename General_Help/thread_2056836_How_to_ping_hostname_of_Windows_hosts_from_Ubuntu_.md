---
title: "How to ping hostname of Windows hosts from Ubuntu desktop"
date: 2012-09-12
forum: General Help
---

### Post by naushadkhan on 2012-09-12
I am very new to Ubuntu. I have installed Ubuntu 12.04 32 bit on my PC. Now when i am trying to ping Windows systems with hostnames I am not able to ping them. And when i try to ping with IP, i am able to ping. 

Please let me know, what should i do to ping hostnames of Windows PC.

Regards,
Naushad Khan

---

### Post by zero2xiii on 2012-09-12
Hay,

You might have to try and set your router (assuming it is the DHCP server) as the DNS server of the ubuntu machine. Or it might be that the hostname is not correct (seeing as the IP ping works.)

Can you please give an example input, expected response and received response? And any other related information (such as the workgroup of the windows machine)

Cherz

---

### Post by timcredible on 2012-09-12
you just need to add the correct dns server to your ubuntu machine, and possibly the correct dns suffix search entries.  find out what they are in windows by "ipconfig /all" and make sure you're using the same server and suffixes in linux (Menu->Preferences->Network Connections)

---

### Post by Colo993 on 2012-09-12
naushadkhan,

When you say you are PINGing windows host names are you using the FQDN or are you using just the NetBIOS host name?  On older windows environments Microsoft circumvented DNS with WINS.  WINS allowed users to PING host names without using the FQDN.  This may seem a little confusing, and as others have pointed out, you may only need to point your Ubuntu PC to the correct DNS servers and setup the correct DNS prefixes.

Colo993

---

### Post by naushadkhan on 2012-09-14
Hi All,

Thanks for your answers. I found that on my IP4 lan settings DNS server was set to 8.8.8.8, hence i changed it to my ADS DNS server and now i am able to ping all windows hosts as well.

Regards,
Naushad Khan

---

### Post by Scott Harrison on 2012-09-14
> **naushadkhan said:**
> Hi All,

Thanks for your answers. I found that on my IP4 lan settings DNS server was set to 8.8.8.8, hence i changed it to my ADS DNS server and now i am able to ping all windows hosts as well.

Regards,
Naushad Khan
Well done. :)

---

