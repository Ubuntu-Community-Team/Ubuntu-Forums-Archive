---
title: "Set up DNS server on VPS tinydns"
date: 2012-07-21
forum: General Help
---

### Post by matimont on 2012-07-21
Hi,

Is there a good guide on how to set up a DNS server with Ubuntu using tinydns?

Also, If I do set up a Name server on my own VPs, will I be able to do reverse DNS? Today, my Cloud HP provider doesn't give me reverse DNS and I'm gettgin this out of mxtoolbox:

*"None of your MX record IP addresses have corresponding reverse DNS entries (PTR records). If these MX records are used to send outgoing mail this will cause them to trip anti spam filters. Many SMTP servers will not accept mail from an IP with no reverse DNS."*


And I'm unable to send to Hotmail for example due to this, i've tried SPF records with no luck, still the same issue.

I've also heard rDNS can only be changed by my provider, so what other suggestions you have for me to get rDNS to work? Should I stay with my previous shared hosting for email while using HP CLoud to host my domains and the databases?

---

