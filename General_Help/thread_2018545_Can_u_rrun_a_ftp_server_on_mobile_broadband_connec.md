---
title: "Can u rrun a ftp server on mobile broadband connection?"
date: 2012-07-06
forum: General Help
---

### Post by Huzi94 on 2012-07-06
Hello,
I am on precise and I am deciding to run a ftp server. I installed vsftpd. But it seems that I am the only one who can access it. My friends aren't able to view the files on my server. Is it because I connect to the Internet using a ZTE modem (mobile broadband connection). My ip address is also quite stange - 10.53.xx.xx

Please help me solve this problem

---

### Post by dcstar on 2012-07-07
> **Huzi94 said:**
> Hello,
I am on precise and I am deciding to run a ftp server. I installed vsftpd. But it seems that I am the only one who can access it. My friends aren't able to view the files on my server. Is it because I connect to the Internet using a ZTE modem (mobile broadband connection). My ip address is also quite stange - 10.53.xx.xx

Please help me solve this problem

10.x.x.x are Private IP addresses not accessible from the Internet:

[https://en.wikipedia.org/wiki/IP_address#IPv4_private_addresses](https://en.wikipedia.org/wiki/IP_address#IPv4_private_addresses)

Talk to your ISP.

---

### Post by Huzi94 on 2012-07-07
> **dcstar said:**
> 10.x.x.x are Private IP addresses not accessible from the Internet:

[https://en.wikipedia.org/wiki/IP_address#IPv4_private_addresses](https://en.wikipedia.org/wiki/IP_address#IPv4_private_addresses)

Talk to your ISP.

is there a way I can use my private address to run a ftp server

I googled "convert private ip address into public" and found something on NAT.

---

### Post by Cheesemill on 2012-07-07
I'm betting there is nothing you can do about it as you having no control over the router doing your NAT (it belongs to your ISP).

It will probably also be against your terms of service to run any kind of server using that connection.

---

