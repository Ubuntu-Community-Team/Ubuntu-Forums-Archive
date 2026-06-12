---
title: "hosting a website using ubuntu"
date: 2012-06-20
forum: General Help
---

### Post by shaikzubair on 2012-06-20
Hello all,

I am new to linux environment and i want to set up a dedicated webserver using my DSL home connection.1

I have a server with ubuntu-server 12 installed with Apache, php, my sql working.

When i go to [http://localhost](http://localhost) i get a mesg "IT WORKS :p".

Now if i  wanted to set up a webserver for ex: [www.1234.com]("http://www.1234.com") what are the things i have to know??

Note: i have dynamic IP, I have port forwarded the router and it has a default firewall. (I knw that certain ISP blocks the port 80 howevr I  have spoke to them n they said that they dont block port 80 and i have also changed the apache port 85 still it does not work from outside.)


MY Questions:

1. Now if i  wanted to set up a web-server for ex: [www.1234.com]("http://www.1234.com") what are the things i have to know??

2. when i enter the external ip address or the address ([www.1234.com]("http://www.1234.com") ) it does not show me my index page.

3.i observed that when i ping the ipaddress or address inside the network i get the reply but when i ping from outside i get "Requested timeout".

---

### Post by hfa2010 on 2012-06-20
You need a global ip, or a DDNS... Try reading this:
[http://dnsknowledge.com/tutorials/centos-tutorials/bind-9/howto-setup-dynamic-dns-ddns/ ]("http://dnsknowledge.com/tutorials/centos-tutorials/bind-9/howto-setup-dynamic-dns-ddns/")
or here:
[http://www.howtoforge.com/fedora_dynamic_dns](http://www.howtoforge.com/fedora_dynamic_dns)
And you need to asign on free service:
[http://www.dnsexit.com/Direct.sv?cmd=dynDNS](http://www.dnsexit.com/Direct.sv?cmd=dynDNS)
[]("http://dnsknowledge.com/tutorials/centos-tutorials/bind-9/howto-setup-dynamic-dns-ddns/")

---

### Post by btindie on 2012-06-20
1. Install ez-ipupdate then sign up for one of the free dyn dns services. See "sudo apt-cache show ez-ipupdate" for a list of supported ones. Some routers have a built in Dynamic DNS client which means you don't need to install this though the number of providers they support can be limited.

2. It won't do as your router won't do an ICMP redirect. Your dynamic public IP address is on the outside of your router and without that there's no way for your internal hosts to get back in. You'd have to add an entry to your /etc/hosts file to create the hostname to private IP mapping. For this to work successfully it's best that your give your webserver a static IP address either via manual configuration or via an unlimited lease on your DHCP server which in your case would be on your 'router'. 

3. Your ISP or your router may drop ICMP traffic.

Make sure that the firewall on your server is either disabled or permits traffic on port 80, by default it may only allow traffic originating from the local subnet.

You can test your connection remotely by using the telnet command
```
$ telnet <my_public_ip> 80
GET / HTTP/1.0


```that should return your page as a HTML document.

---

### Post by shaikzubair on 2012-06-20
> **hfa2010 said:**
> 
You need a global ip, or a DDNS... Try reading this:
[http://dnsknowledge.com/tutorials/centos-tutorials/bind-9/howto-setup-dynamic-dns-ddns/](http://dnsknowledge.com/tutorials/centos-tutorials/bind-9/howto-setup-dynamic-dns-ddns/)



I dont understand why do i need to install DHCP server???

> **hfa2010 said:**
> 

or here:
[http://www.howtoforge.com/fedora_dynamic_dns](http://www.howtoforge.com/fedora_dynamic_dns)



I have installed BIND 9 as stated here: 

```
http://comtech247.net/2012/04/30/how-to-set-up-a-dns-server-on-ubuntu-server-12-04-lts/
```BIND 9 starts with no problem.

> **hfa2010 said:**
> 
And you need to asign on free service:
[http://www.dnsexit.com/Direct.sv?cmd=dynDNS](http://www.dnsexit.com/Direct.sv?cmd=dynDNS)


I have signed up with no-ip.com and i have installed noip2 client and it updates every 5 mins.


----------------------------------------------------------
|Still I am unable to access webpage from outside.|
-----------------------------------------------------------

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

> ** btindie said:**
>  2. It won't do as your router won't do an ICMP redirect. Your dynamic  public IP address is on the outside of your router and without that  there's no way for your internal hosts to get back in. You'd have to add  an entry to your /etc/hosts file to create the hostname to private IP  mapping. For this to work successfully it's best that your give your  webserver a static IP address either via manual configuration or via an  unlimited lease on your DHCP server which in your case would be on your  'router'. 

i use NETGEAR DG834GB router and i see that it has builtin dyndns option but i cannot do that because i cannot signup for a free host.


> ** btindie said:**
>  
Make sure that the firewall on your server is either disabled or permits  traffic on port 80, by default it may only allow traffic originating  from the local subnet.

You can test your connection remotely by using the telnet command
     Code:
     $ telnet <my_public_ip> 80 GET / HTTP/1.0 
that should return your page as a HTML document.      


I am nt sure about telnet bt i use ssh. I am sorry i should have stated before.

---

