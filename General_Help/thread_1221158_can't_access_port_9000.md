---
title: "can't access port 9000"
date: 2009-07-23
forum: General Help
---

### Post by jfrankov on 2009-07-23
Hi,

I'm running a mongrel_cluster on ports 9000-9002 on Ubuntu 8.04.1 (hosted on a Linode). I have a rails app running on these ports but when I try to access them in my browser I get a "can't establish a connection to the server at foo.com:9000" error.

When I do a netstat -a | grep 9000 it returns nothing. I tried these commands:

sudo ufw enable; sudo ufw allow 9000
sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 9000 -j ACCEPT

What am I missing?

Thanks for any and all help- I'm not much of a firewall guy :confused:

-Jason

---

