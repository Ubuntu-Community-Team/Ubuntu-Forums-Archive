---
title: "Internet super slow due to DNS issue Help"
date: 2006-03-08
forum: General Help
---

### Post by shade73 on 2006-03-08
Ok, So I've determined that one of my DNS servers is only used for internal purposes, that the internal local one times out before hitting the 2nd server to grab the actual internet addy.  This leads to huge lag times before the page ever starts to load (15 - 20 seconds of nothing).  It grabs this address from DHCP, so I can't change it.  I know on windows the same thing happens but it only takes a second and the page is up. Do i need to set a setting differently?  Maybe change the DNS timeout to be alot faster?  Where would I change that?  Any help would be greatly appreciated!

Thanks

---

### Post by mr.p on 2006-03-08
[QUOTE=shade73]Ok, So I've determined that one of my DNS servers is only used for internal purposes, that the internal local one times out before hitting the 2nd server to grab the actual internet addy.  This leads to huge lag times before the page ever starts to load (15 - 20 seconds of nothing).  It grabs this address from DHCP, so I can't change it.  I know on windows the same thing happens but it only takes a second and the page is up. Do i need to set a setting differently?  Maybe change the DNS timeout to be alot faster?  Where would I change that?  Any help would be greatly appreciated!

Thanks[/QUOTE]

What router are you using in particular?

---

### Post by lamego on 2006-03-08
You can setup your dns servers on /etc/resolv.conf and then disable the dhcp client from getting the dns servers:
```
sudo gedit /etc/dhcp3/dhclient.conf
```
remove the "domain-name-servers" from the request list.

---

### Post by Dafydd on 2006-04-05
[QUOTE=lamego]You can setup your dns servers on /etc/resolv.conf and then disable the dhcp client from getting the dns servers:
```
sudo gedit /etc/dhcp3/dhclient.conf
```
remove the "domain-name-servers" from the request list.[/QUOTE]


This doesn't work on my machine. I've tried what u suggested and then did  "  
/etc/init.d/networking restart " but still getting the same problem.

This is one of about 5 or 6 annoying things about Ubuntu that make me want to switch back to Windows or at least something better...

dafydd

---

### Post by Dafydd on 2006-04-05
Also if i follow your instructions (which i have unfortunately) i'll ahve to fiddle with the conf files again tomorrow when i swap wireless networks two or three times.

it's all such a struggle with ubuntu

---

