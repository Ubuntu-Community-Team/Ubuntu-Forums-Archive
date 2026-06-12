---
title: "resolv.conf after dhcp"
date: 2009-07-09
forum: General Help
---

### Post by statistic on 2009-07-09
So I currently have a version of resolv.conf per-cooked to use open-dns, however trying to get that into my resolv.conf after dhcp has been done, is proving to be a challenge. In case you're wondering why, it's to dodge the dns changing I'm getting from my router and and my ISP (they both do it at two different levels so it's everywhere).

I have a script in /etc/dhcp3/dhclient-exit-hooks.d that tries to copy the good resolv.conf over the one the /etc/ but it doesn't seem to work. The script also after copying the file makes a remote port forward, and it does that successfully as root, but /etc/resolv.conf remains unchanged.

The only thing I would guess is that it's copying before network manager updates the file. Any help to get me past this would be great thank you.

---

### Post by HermanAB on 2009-07-09
You can configure dhclient to add more schtuff to the resolv.conf file.  Read the dhclient man page.

---

### Post by statistic on 2009-07-09
Thanks for the tip. So I tried adding "supersede 208.67.222.222, 208.67.220.220;" to /etc/dhcp3/dhclient.conf but no luck. I'm going to keep poking, but if you know what I'm trying to do, please do tell.

Thanks again.

---

### Post by statistic on 2009-07-09
My bad, it actually did work, I jsut had a type when I put it in the conf file.

However I'm now also trying to remove the line "search mygateway.net" from the file, but am unsure of which option it is.

---

### Post by statistic on 2009-07-09
alright so everything is happy now:

```
supersede domain-name-servers 208.67.222.222, 208.67.220.220;
supersede domain-name otherDomain.ca

```

---

