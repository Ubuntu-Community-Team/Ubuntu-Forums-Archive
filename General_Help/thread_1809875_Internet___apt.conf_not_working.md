---
title: "Internet  / apt.conf not working"
date: 2011-07-22
forum: General Help
---

### Post by mswamy78 on 2011-07-22
Hello,

I am using ubuntu  9.1 on evaluation board and my internet is not working. Also i need to install softwares and apt-get install is also not working.


Under /etc/apt/apt.conf....i have configured as below..

Acquire::http::proxy "http://username:passwd@proxyserver:8080/";
Acquire::ftp::proxy "ftp://username:passwd@proxyserver:8080/";
Acquire::https::proxy "https://username:passwd@proxyserver:8080/";

If I do ifconfig...inet address was not configured and I forcefully configured it using 
sudo ifconfig eth2 10.246.80.15 up 
 


Kindly help.

Thanks,
Swamy

---

### Post by galvatron408 on 2011-07-22
yes, thats correct. apt needs the internet. maybe you should try 11.04.

---

### Post by dagamant on 2011-07-22
What eval board are you using? what kind of network interface does it have? the problem right now is not apt, it is the network. run ifconfig and paste the output here so we can see.

---

