---
title: "cannot load certain websites"
date: 2010-09-30
forum: General Help
---

### Post by rre12 on 2010-09-30
This is a remade thread from [http://ubuntuforums.org/showthread.php?p=9898363#post9898363](http://ubuntuforums.org/showthread.php?p=9898363#post9898363) because I wanted to change the name to something more general. So for some reason I cannot load certain websites such as yahoo.com. I tried ubuntu, kubuntu, fedora, mint gnome, and LMDE. They are all having the same issue. I am dual booting with Windows 7 and everything is fine on there. I have tried disabling IPv6 and that didn't fix it. :(

---

### Post by rre12 on 2010-10-01
I seem to have solved this by using openDNS. Why do I need to use this just to browse some sites?

---

### Post by mrhhug on 2010-10-01
if you leave you DNSs blank your isp should provide then for you. - i think google offers a free dns too

---

### Post by rre12 on 2010-10-01
So Ubuntu's default to not having any DNS?

---

### Post by rre12 on 2010-10-01
So Ubuntu does not have a preset DNS after an installation?

---

### Post by mrhhug on 2010-10-01
if you are set to DHCP, then nameservers and gateways should be automatically set.

edit them yourself if you choose they reside in ```
/etc/resolv.conf
```

you do need these things(gateways and nameservers) if you want to use words instead of numbers, networking is all numbers, and the words are used to make is easier for you. these DNS servers convert the words to numbers for you automatically.

most people are gonna have a router in their home, and the router will do all the dirty work of getting and updating your DNS - your router = DHCP server.

recap:
1) you ISP usually provides the DNS servers
2) there are also other free DNS servers - modify your /etc/resolv.conf
3) if you are set to automatically obtain ip (DHCP) DNS server are included in that - see number 1
4) DNS servers convert your English or Spanish or Mandarin or Chhattisgarhi into numbers that computers can understand.

---

