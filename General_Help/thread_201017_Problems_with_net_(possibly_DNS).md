---
title: "Problems with net (possibly DNS)"
date: 2006-06-21
forum: General Help
---

### Post by Xilon on 2006-06-21
I just turned on my PC and tried to browse teh net but was unable to, it was as if I had no net, but my IM was working... I tried pinging google.com but it said that teh host could not be resolved so I tried getting google's IP from another computer and pinged that, surprise surprise it worked!

I have no idea why my DNS doesn't work right now but is there any way to restart or start it? Anyone know how to fix this problem? :(

---

### Post by Xilon on 2006-06-21
ok it's worse than I thought :S I decided to just format since I was  getting a bit sick of amd64 support and installed ubuntu 32bit, the liveCD worked fine with the net but when I went into the install it didn't work again! I still can't resolve hostnames :( Is this a hardware thing?

---

### Post by droazen on 2006-06-25
Are you getting your ISP's DNS server addresses using dhclient from a dhcp server, or through pppd? If you know the IP address of your ISP's DNS server you could always hardcode it in /etc/resolv.conf, and set its permissions so that no process can  write to that file...

---

### Post by ayoli on 2006-06-25
you also got the graphical way thru main menu System > Administration > Network, then pick the DNS tab and add here the DNS IPs provided by your ISP or your router ip if you have a dynamic ip set by yourrouter's dhcp

---

