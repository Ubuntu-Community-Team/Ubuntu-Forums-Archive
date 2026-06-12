---
title: "iptables question"
date: 2006-03-06
forum: General Help
---

### Post by rockit on 2006-03-06
I have a question concerning iptables... 
In debian/ubuntu... can you filter by domain name in iptables? 

I realize that it depends on what order everything is loaded at startup and if you have DNS configured properly on the firewall, but this is where I start getting confused. I know that some distributions like Fedora load iptables before the network is brought up (or at least that's my understanding...I've been known to be wrong before though ;-) )which ultimately means that filtering by domain isn't possible because of DNS not being available at first. After the network is brought up though, is this still an issue? 

Thanks ahead of time

---

### Post by steve.horsley on 2006-03-06
From **man iptables**:
>        -s, --source [!] address[/mask]
              Source specification.  Address can be either a network name, a hostname (please note that specifying  any  name  to  be
              resolved  with  a  remote  query  such  as  DNS is a really bad idea), a network IP address (with /mask), or a plain IP
              address.  The mask can be either a network mask or a plain number, specifying the number of 1&#8217;s at the left side of the
              network  mask.   Thus,  a  mask  of 24 is equivalent to 255.255.255.0.  A "!" argument before the address specification
              inverts the sense of the address. The flag --src is an alias for this option.


So yes you can, but it's  Really Bad Idea.

---

