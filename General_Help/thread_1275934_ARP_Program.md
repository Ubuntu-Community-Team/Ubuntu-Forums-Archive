---
title: "ARP Program"
date: 2009-09-26
forum: General Help
---

### Post by Psycho.mario on 2009-09-26
Is there a way i can find out a computers IP from their mac address from Ubuntu? Maybe by creating ARP packets then monitoring with wireshark? Does anyone know how i would go about doing this? Thanks

P.S. I don't want to use hostnames because then i need DNS

---

### Post by Psycho.mario on 2009-09-28
Bump

---

### Post by doas777 on 2009-09-28
check out this post.

[http://www.linuxquestions.org/questions/linux-networking-3/how-to-find-ip-address-of-a-machine-if-i-know-their-mac-address-353239/#post1800448](http://www.linuxquestions.org/questions/linux-networking-3/how-to-find-ip-address-of-a-machine-if-i-know-their-mac-address-353239/#post1800448)

---

### Post by Psycho.mario on 2009-09-28
Perfect, thanks.
My script so far:
```
#!/bin/bash
echo "Please enter your broadcast address..."
read broadcast
ping -b -c1 $broadcast 2>/dev/null 1>/dev/null
echo "Please enter the mac you are looking for...[xx:xx:xx:xx:xx:Xx]"
read mac
arp -a | grep $mac
exit 0
```
Works perfectly, but i'm going to add in some more fancy stuff

Thanks

---

