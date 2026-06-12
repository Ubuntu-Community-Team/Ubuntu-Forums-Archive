---
title: "call web instead of ip with name"
date: 2011-06-08
forum: General Help
---

### Post by Rakeshvijayan on 2011-06-08
Dear friends please find me a solution ...

My problem is, On my Institution we are using a library management software name koha it installed on ubuntu it works fine .. .we call it web page by our system ipaddress 192.168.1.200:8000 we want to call this page with a name .Is it possible for  me.........
I searched about this ,but no way

---

### Post by Joe of loath on 2011-06-08
You'll need an internal DNS server, although I'm not totally sure how well that would work on an internal network, as opposed to  the internet.

---

### Post by lz1dsb on 2011-06-08
There's no difference for the DNS server whether it's in a local network in the internet. The internal DNS server should be configured though to synchronize with the dns servers in the internet, or act as a proxy for any other DNS request. 
But the easiest thing to do would be to just edit the local hosts file on your machines. Each linux machine consults first its local hosts file before sending a DNS request.


Cheers, 
Boyan

---

### Post by Joe of loath on 2011-06-08
> **lz1dsb said:**
> 
But the easiest thing to do would be to just edit the local hosts file on your machines. Each linux machine consults first its local hosts file before sending a DNS request.

Good call, forgot about that :p

---

### Post by Rakeshvijayan on 2011-06-09
> **lz1dsb said:**
> There's no difference for the DNS server whether it's in a local network in the internet. The internal DNS server should be configured though to synchronize with the dns servers in the internet, or act as a proxy for any other DNS request. 
But the easiest thing to do would be to just edit the local hosts file on your machines. Each linux machine consults first its local hosts file before sending a DNS request.


Cheers, 
Boyan


is it enough to edit the local hosts for my problem, with a [www.example.com](www.example.com)

---

### Post by Rakeshvijayan on 2011-06-09
Thanks issue solve by editing hosts Thanks again ............

---

### Post by Rakeshvijayan on 2011-06-09
Ho sorry friends its only allow to call on the local system .when I call web page on another system it show server not found 

leave your suggestion

---

### Post by linuxinstalledfromhdd on 2011-06-09
Did you set up your own DNS server? Did you update it from a master list?

---

### Post by Rakeshvijayan on 2011-06-29
This is my whole configuration of DNS I think its not working I just it on my desktop pc

---

### Post by Rakeshvijayan on 2011-06-29
remaining portions of DNS

---

### Post by Rakeshvijayan on 2011-06-29
I have one doubt I am using netword 192.168.1.0 and my ip is 192.168.1.100 . so In my reverse address I gave as 0.168.192 is this is wrong for me ?give any suggestion....

---

### Post by Habitual on 2011-06-30
```
sudo vi /etc/hosts
``` and add
192.168.1.200       koha koha

```
sudo service network restart
```

done.

[http://koha](http://koha) should now bring up 192.168.1.200

---

### Post by Rakeshvijayan on 2011-07-11
> **Habitual said:**
> ```
sudo vi /etc/hosts
``` and add
192.168.1.200       koha koha

```
sudo service network restart
```done.

[http://koha](http://koha) should now bring up 192.168.1.200


By this way we can  call only in local host system . my problem resolved by DNS but another issue arise  I can call web page [www.mctlib.com](www.mctlib.com) with port address 8080 I want to remove the port .what file that I want to edit on appache

---

