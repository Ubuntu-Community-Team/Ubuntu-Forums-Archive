---
title: "can't download php5 using ubuntu server"
date: 2011-11-19
forum: General Help
---

### Post by eltiti55555 on 2011-11-19
As the tittle says php5 fails to install on my Ubuntu server, which I am using through virtual box. I am supposed to download php5 on my server and then from my Desktop Ubuntu also running on Virtual Box I am supposed to access a php page, anyways I haven't got that far since I can't even get php working. I added a NAT interface to the Ubuntu server and I configured it to use DHCP so it now connects to the internet without any problems, I can ping Google with success and I can even access Google using a text-based browser. Here is a screenshot of my problem.

[IMG]http://imageshack.us/photo/my-images/841/50059033.jpg/[/IMG] [http://imageshack.us/photo/my-images/841/50059033.jpg/](http://imageshack.us/photo/my-images/841/50059033.jpg/)

PS: sudo apt-get install php5  (this is the right command to get php into your system right?)

---

### Post by n00b2u on 2011-11-19
I think your pic didn't get posted(maybe I am missing something), however here is a good wiki article on the subject.  Hope this helps:

[http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-11.04-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-11.04-lamp)

---

### Post by ikt on 2011-11-19
It looks as though your package list might be out of date or the mirror is out of date.

First try

sudo apt-get update

Then sudo apt-get upgrade

then upgrade the packages and see if you can install php5.

If that doesn't work try changing the mirror to a different one:

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by eltiti55555 on 2011-11-19
> **n00b2u said:**
> I think your pic didn't get posted(maybe I am missing something), however here is a good wiki article on the subject.  Hope this helps:

[http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-11.04-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-11.04-lamp)

There should be a link to the pic i upload on my post, you should be able to see it. :S

---

### Post by eltiti55555 on 2011-11-19
> **n00b2u said:**
> I think your pic didn't get posted(maybe I am missing something), however here is a good wiki article on the subject.  Hope this helps:

[http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-11.04-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-11.04-lamp)

Do I really need to install mySQL and Apache before installing php?

> **ikt said:**
> It looks as though your package list might be out of date or the mirror is out of date.

First try

sudo apt-get update

Then sudo apt-get upgrade

then upgrade the packages and see if you can install php5.

If that doesn't work try changing the mirror to a different one:

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

I have a similar program with "sudo apt-get update", it just hangs :S

---

### Post by fragos on 2011-11-19
I don't know if this is your problem but you require a bit of configuration to run PHP code once PHP is installed. The file to be edited is /etc/apache2/httpd.conf. If it's already there it's probably empty, if not create it. Place the following three lines in it. The

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

The web server will have to restart for the configuration changes to take effect. The next time your sytem boots will do that or run the following CLI.

sudo /etc/init.d/apache2 restart

---

### Post by eltiti55555 on 2011-11-19
> **fragos said:**
> I don't know if this is your problem but you require a bit of configuration to run PHP code once PHP is installed. The file to be edited is /etc/apache2/httpd.conf. If it's already there it's probably empty, if not create it. Place the following three lines in it. The

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

The web server will have to restart for the configuration changes to take effect. The next time your sytem boots will do that or run the following CLI.

sudo /etc/init.d/apache2 restart

I can't even get php installed, I tried downloading the mySQL program just to try something different and I think I am getting the same problem. What should I do?

[http://imageshack.us/photo/my-images/254/49632294.jpg/]("http://imageshack.us/photo/my-images/254/49632294.jpg/")

---

### Post by boblemur on 2011-11-19
try running
```
dig ca.archive.ubuntu.com
```
the result you want is something like:
```
$ dig ca.archive.ubuntu.com

; <<>> DiG 9.7.3 <<>> ca.archive.ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 57666
;; flags: qr rd ra; QUERY: 1, ANSWER: 14, AUTHORITY: 3, ADDITIONAL: 3

;; QUESTION SECTION:
;ca.archive.ubuntu.com.		IN	A

;; ANSWER SECTION:
ca.archive.ubuntu.com.	600	IN	A	91.189.88.31
ca.archive.ubuntu.com.	600	IN	A	91.189.88.40
ca.archive.ubuntu.com.	600	IN	A	91.189.88.45
ca.archive.ubuntu.com.	600	IN	A	91.189.88.46
ca.archive.ubuntu.com.	600	IN	A	91.189.92.169
ca.archive.ubuntu.com.	600	IN	A	91.189.92.170
ca.archive.ubuntu.com.	600	IN	A	91.189.92.176
ca.archive.ubuntu.com.	600	IN	A	91.189.92.177
ca.archive.ubuntu.com.	600	IN	A	91.189.92.179
ca.archive.ubuntu.com.	600	IN	A	91.189.92.180
ca.archive.ubuntu.com.	600	IN	A	91.189.92.181
ca.archive.ubuntu.com.	600	IN	A	91.189.92.182
ca.archive.ubuntu.com.	600	IN	A	91.189.92.183
ca.archive.ubuntu.com.	600	IN	A	91.189.92.184

;; AUTHORITY SECTION:
ubuntu.com.		163704	IN	NS	ns3.canonical.com.
ubuntu.com.		163704	IN	NS	ns1.canonical.com.
ubuntu.com.		163704	IN	NS	ns2.canonical.com.

;; ADDITIONAL SECTION:
ns1.canonical.com.	163589	IN	A	91.189.94.173
ns2.canonical.com.	163589	IN	A	91.189.94.219
ns3.canonical.com.	163589	IN	A	209.6.3.210

;; Query time: 347 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sun Nov 20 10:45:14 2011
;; MSG SIZE  rcvd: 375


```

---

### Post by eltiti55555 on 2011-11-19
> **boblemur said:**
> try running
```
dig ca.archive.ubuntu.com
```
the result you want is something like:
```
$ dig ca.archive.ubuntu.com

; <<>> DiG 9.7.3 <<>> ca.archive.ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 57666
;; flags: qr rd ra; QUERY: 1, ANSWER: 14, AUTHORITY: 3, ADDITIONAL: 3

;; QUESTION SECTION:
;ca.archive.ubuntu.com.		IN	A

;; ANSWER SECTION:
ca.archive.ubuntu.com.	600	IN	A	91.189.88.31
ca.archive.ubuntu.com.	600	IN	A	91.189.88.40
ca.archive.ubuntu.com.	600	IN	A	91.189.88.45
ca.archive.ubuntu.com.	600	IN	A	91.189.88.46
ca.archive.ubuntu.com.	600	IN	A	91.189.92.169
ca.archive.ubuntu.com.	600	IN	A	91.189.92.170
ca.archive.ubuntu.com.	600	IN	A	91.189.92.176
ca.archive.ubuntu.com.	600	IN	A	91.189.92.177
ca.archive.ubuntu.com.	600	IN	A	91.189.92.179
ca.archive.ubuntu.com.	600	IN	A	91.189.92.180
ca.archive.ubuntu.com.	600	IN	A	91.189.92.181
ca.archive.ubuntu.com.	600	IN	A	91.189.92.182
ca.archive.ubuntu.com.	600	IN	A	91.189.92.183
ca.archive.ubuntu.com.	600	IN	A	91.189.92.184

;; AUTHORITY SECTION:
ubuntu.com.		163704	IN	NS	ns3.canonical.com.
ubuntu.com.		163704	IN	NS	ns1.canonical.com.
ubuntu.com.		163704	IN	NS	ns2.canonical.com.

;; ADDITIONAL SECTION:
ns1.canonical.com.	163589	IN	A	91.189.94.173
ns2.canonical.com.	163589	IN	A	91.189.94.219
ns3.canonical.com.	163589	IN	A	209.6.3.210

;; Query time: 347 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sun Nov 20 10:45:14 2011
;; MSG SIZE  rcvd: 375


```

No, I don't get none of those servers, it says that no servers could be reached.Check this picture for more detailed. 

[http://imageshack.us/photo/my-images/10/31197704.jpg/]("http://imageshack.us/photo/my-images/10/31197704.jpg/")

---

### Post by boblemur on 2011-11-19
that picture suggest that you dont have DNS working at all. 

try running:
```
cat /etc/resolv.conf
``` 
you should get something like:
```
cat /etc/resolv.conf 
domain home
search home
nameserver 192.168.1.1
```

then try running (but replace the address with the one you got above):
```
ping -c 1 192.168.1.1
```

also try running (you dont need to provide a picture of this just check to see if you get server addresses or not):
```
dig www.google.com
```

---

### Post by eltiti55555 on 2011-11-19
> **boblemur said:**
> that picture suggest that you dont have DNS working at all. 

try running:
```
cat /etc/resolv.conf
``` 
you should get something like:
```
cat /etc/resolv.conf 
domain home
search home
nameserver 192.168.1.1
```

then try running (but replace the address with the one you got above):
```
ping -c 1 192.168.1.1
```

also try running (you dont need to provide a picture of this just check to see if you get server addresses or not):
```
dig www.google.com
```

Pinging the address from that file fails and the dig command can't reach the google server.

---

### Post by boblemur on 2011-11-19
ok so then your vm has lost its internet connection. I noticed from the picture you uploaded last that you have two network interfaces.

eth1: 192.168.0.101
eth0: 10.0.2.15

do you know why you have two?

can you post the output of ```
route -n
```

What subnet do you use for your local network? eg mine is 192.168.1.*

and what was the ip address inside /etc/resolv.conf?

---

### Post by eltiti55555 on 2011-11-19
> **boblemur said:**
> ok so then your vm has lost its internet connection. I noticed from the picture you uploaded last that you have two network interfaces.

eth1: 192.168.0.101
eth0: 10.0.2.15

do you know why you have two?

can you post the output of ```
route -n
```

What subnet do you use for your local network? eg mine is 192.168.1.*

and what was the ip address inside /etc/resolv.conf?

No,I still have internet because I can ping google, youtube, facebook,etc. Here have a look at this: [http://imageshack.us/photo/my-images/696/66691075.jpg/]("http://imageshack.us/photo/my-images/696/66691075.jpg/")

Give me some popular ip address to test. I do think the dns is down because when I pig [www.google.com](www.google.com) none of the packet reach. I have 2 adapters, one is an internal adapter and the other one is NAT adapter. I need the intnet adapter to connect between the virtual desktop and the server, and obviously the NAT to connect to the internet.

---

### Post by boblemur on 2011-11-19
ok so your dns settings (in /etc/resolv.conf) seem like they might be set for the wrong gateway, if you run

```
route -n
```

you will see something like this:

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 lan
121.209.208.0   0.0.0.0         255.255.248.0   U     0      0        0 telstra
0.0.0.0         121.209.208.1   0.0.0.0         UG    100    0        0 telstra

```

the entry you are interested in is the last entry. the one that starts with 0.0.0.0 (which is your default gateway). 

This is set correctly because you can reach the internet. so take the ip address in the 2nd column, in my case it would be the address 121.209.208.1 and put that in /etc/resolv.conf

so it should look like:
```
nameserver 121.209.208.1
```
in that file then try ping a website by its dns name and see if it now resolves.

---

### Post by boblemur on 2011-11-19
just to point out this assumes that your default gateway is a dns server (you should try putting your routers IP address there if your default gateway isnt a dns server).

---

### Post by eltiti55555 on 2011-11-19
> **boblemur said:**
> just to point out this assumes that your default gateway is a dns server (you should try putting your routers IP address there if your default gateway isnt a dns server).

Tried both ways and neither worked, now my ubuntu client has the same issue. Firefox won't go to [www.google.com](www.google.com), but if I enter 74.125.224.72 it will. One thing I do notice is that if I disable the intnet adapter(I have an intnet adapter on both client and serrver) on VirtualBox and only leave the NAT adapter the DNS starts to work again and I can type [www.google.com](www.google.com) normally.

---

### Post by boblemur on 2011-11-19
ok and when they are disabled what functionality are you missing? or does that solve your issue?

---

### Post by eltiti55555 on 2011-11-19
> **boblemur said:**
> ok and when they are disabled what functionality are you missing? or does that solve your issue?

It solves my issue on the desktop, but then I can't ping the server, which means I can't connect to it. I was supposed to add intnet adapters to both the server and client to be able to mount samba shares. It is all part of an school assignment. If it comes to it I will upload the word file that says what I have to do.

---

### Post by boblemur on 2011-11-19
ok so on the client that the dns works cat the /etc/resolv.conf file and take the ip address from there then turn them both back on and then update the files to back to that value. It should work with that set to what it is when it works. 

The other issue is that it might be that both interfaces are trying to access the same subnet. 

so make sure that you dont have any overlapping ip addresses so for example if you have 192.168.0.102 as your internal one but also as your real LAN addresses then it will not know how to get to the one outside the vm. 

whats your LAN subnet,
whats the VM subnet,
whats the NAT subnet?

---

### Post by fragos on 2011-11-19
> **eltiti55555 said:**
> Do I really need to install mySQL and Apache before installing php?



I have a similar program with "sudo apt-get update", it just hangs :S

You do need to install apache2 but not mysql.

The only thing that should interfere with apt-get is if you're running another package that accesses dpkg like for instance synaptic or Software Center. Have you tried a reboot of your system? That can sometimes solve strange problems like the one you have.

---

### Post by boblemur on 2011-11-19
> **fragos said:**
> You do need to install apache2 but not mysql.

The only thing that should interfere with apt-get is if you're running another package that accesses dpkg like for instance synaptic or Software Center. Have you tried a reboot of your system? That can sometimes solve strange problems like the one you have.

If you read through the posts above you will see that the issue is that apt-get is unable to resolve the DNS name for ca.archive.ubuntu.com what package he is installing shouldn't be relevant the issue remains that he cannot connect to the repositories

---

### Post by eltiti55555 on 2011-11-22
> **boblemur said:**
> If you read through the posts above you will see that the issue is that apt-get is unable to resolve the DNS name for ca.archive.ubuntu.com what package he is installing shouldn't be relevant the issue remains that he cannot connect to the repositories

I disabled the intnet virtual adapter and now the DNS(which I assume was causing my problem) is working again. The thing is I shouldn't need to disable my intnet adapter when I need to update packages and enable it back again when I want to connect between the two virtual machines (Server and Client), there should be some sort of fix to my problem. :S

---

