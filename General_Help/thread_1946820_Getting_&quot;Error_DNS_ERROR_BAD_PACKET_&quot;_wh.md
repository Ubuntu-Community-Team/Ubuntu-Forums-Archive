---
title: "Getting &quot;Error: DNS_ERROR_BAD_PACKET &quot; while joining ubuntu 11.10  to domain 2003"
date: 2012-03-25
forum: General Help
---

### Post by sunnysthakur on 2012-03-25
Hello,

Today i installed likewise on my one of my ubuntu 11.10 desktop and want to join the same to AD 2003. But on doing the same i am getting an error.

[FONT=Verdana][SIZE=1][COLOR=Red]lab225@lab225-system-product-name:/var/log$ sudo domainjoin-cli --loglevel verbose join chd Administrator
Joining to AD Domain:   chd
With Computer DNS Name: lab225-system-product-name.chd

Administrator@CHD's password: 

Error: DNS_ERROR_BAD_PACKET [code 0x0000251e]

A bad packet was received from a DNS server. Potentially the requested address does not exist.
lab225@lab225-system-product-name:/var/log$ sudo domainjoin-cli leave
Leaving AD Domain:   (unknown)
SUCCESS
lab225@lab225-system-product-name:/var/log$ sudo domainjoin-cli --loglevel verbose join chd Administrator
Joining to AD Domain:   chd
With Computer DNS Name: lab225-system-product-name.chd[/COLOR][/SIZE][/FONT]

My domain information is as below.

**AD Computer name :-** vs.chd
**Domain Name :-  **        chd
**IP                  : -**          10.0.0.1

I am using the below information in the files edited for like wise.

**/etc/hosts**
10.0.0.1     vs

**/etc/resolv.conf**
search chd
nameserver 10.0.0.1

**/etc/nsswitch.conf**
hosts: files dns mdns4

**/etc/dhcp3/dhcpclient.conf**
supersede domain-name "chd";
prepend domain-name-servers 10.0.0.1;

After configured all these settings i am not able to join AD on Win 2003
[B]
NOTE :-[/B] We have a Gateway where proxy is setup and net is working if setup proxy [IP: 10.0.0.5 with port 80] on every browsers on PC. Is this also a reason that this is not working as same thing is working fine in another lab.

---

### Post by TechKat on 2012-11-21
Not sure if you still have the issue but here is a link that fixed it with my computer:

[http://is101507.students.fhstp.ac.at/?p=128](http://is101507.students.fhstp.ac.at/?p=128)

took me ages to find it and hope this may help some people. :)

---

