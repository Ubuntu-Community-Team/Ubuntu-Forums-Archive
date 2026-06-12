---
title: "Slow Internet"
date: 2010-10-20
forum: General Help
---

### Post by fabricio.lemos on 2010-10-20
I'm having problems with my internet connection. Firefox was really slow but I fix its problem setting network.dns.disableIPv6;true. Google Chrome runs fast by default.

But I still having problems with other software, like curl. Any curl request takes 20 seconds to return in Ubuntu. With Windows they return instantly. I also have some Java code that does some http requests, which also takes 20 seconds and in Windows returns instantly.

I already tried 
```

echo 'blacklist ipv6' | sudo tee -a '/etc/modprobe.d/blacklist.local' >/dev/null
echo "#disable ipv6" | sudo tee -a /etc/sysctl.conf
echo "net.ipv6.conf.all.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
echo "net.ipv6.conf.default.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
echo "net.ipv6.conf.lo.disable_ipv6 = 1" | sudo tee -a /etc/sysctl.conf
```

with no results.

command:
```
cat /proc/sys/net/ipv6/conf/all/disable_ipv6
```
returns 1

and
```
lsmod | grep ipv6
```
returns nothing

Does anyone have some clue on what could be wrong? I'm using Ubuntu 10.10 but also had this problem with 10.04

---

### Post by soldier1st on 2010-10-22
disabling ip6 will not speed up the connection except in rare instances like if it is actaully the cause which is unlikely. also did you try to input another dns server in your network settings like google or opendns?also what all are you running that is accessing the network?i would suggest looking into what all is accessing the network by going into System/Administration/Network Tools and look for the Netstat tab.

---

### Post by fabricio.lemos on 2010-10-23
That was it. I changed my dns to opendns and now it's working just fine. Thank you very much soldier1st.

By the way, I thought it was a problem with ipv6 because firefox was really slow before I disable it in about:config.

---

