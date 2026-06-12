---
title: "double domain name"
date: 2011-09-30
forum: General Help
---

### Post by britesc on 2011-09-30
Hi,

I thought I had setup 11.04 OK (obviously a newbie), but every so often I would get my server showing itself as 
SERVER.company.com.company.com rather than SERVER.company.com

I looked at the various hostname, domainname ,dnsdomainname progs and each reported SERVER.company.com
I then tried hostname -A and voila I get SERVER.company.com.company.com

Could someone please tell me which file I have bodged so I can get the correct FQDN every time.

Thanks and kind regards,

jB  :confused:

---

### Post by aeiah on 2011-09-30
[COLOR="DeepSkyBlue"] SERVER.company.com[/COLOR][COLOR="SeaGreen"][COLOR="Red"].company.com[/COLOR][/COLOR]

the first part is the hostname, the 2nd part is the domain. hostname -A gives you the full thing. you probably just need to use SERVER as the hostname

---

