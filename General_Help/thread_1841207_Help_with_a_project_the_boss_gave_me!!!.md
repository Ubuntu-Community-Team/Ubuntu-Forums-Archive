---
title: "Help with a project the boss gave me!!!"
date: 2011-09-09
forum: General Help
---

### Post by 04prixgt04 on 2011-09-09
Hi,

I am new here and need some help. I have been using ubuntu for the last 6 months and love it. I work at an asnwering service and have been givin a task . The owner of the company wants me to creat a disk that our home operators can use. Want we need to do is create a disk with the following things...


[LIST]
[*]Boot their machines from a non-writeable CD. (ubuntu?) (the operating system is not to be installed on there system. boot and run from disk only)
[*]The booted system should include
[LIST]
[*]  the ability to VPN into the ***** network (pretty sure ubuntu has this capability out-of-the-box)
[*] an IM client
[LIST]
[*] compatible with Spark/XMPP (for now)
[*] using a "toaster" notification interface
[/LIST]
 
[*] An Remote Desktop Connection (RDC) client for logging  into a startel terminal PC (ubuntu supposedly supports the RDP protocol  out-of-the-box)
[/LIST]
 
[*] Document the minimum system requirements for successfully running this CD-based OS to work remotely
[/LIST]
Is this possable>? thanx soooo much in advance.

---

### Post by dcstar on 2011-09-09
> **04prixgt04 said:**
> Hi,

I am new here and need some help. I have been using ubuntu for the last 6 months and love it. I work at an asnwering service and have been givin a task . The owner of the company wants me to creat a disk that our home operators can use. Want we need to do is create a disk with the following things...


[LIST]
[*]Boot their machines from a non-writeable CD. (ubuntu?) (the operating system is not to be installed on there system. boot and run from disk only)
[*]The booted system should include
[LIST]
[*]  the ability to VPN into the ***** network (pretty sure ubuntu has this capability out-of-the-box)
[*] an IM client
[LIST]
[*] compatible with Spark/XMPP (for now)
[*] using a "toaster" notification interface
[/LIST]
 
[*] An Remote Desktop Connection (RDC) client for logging  into a startel terminal PC (ubuntu supposedly supports the RDP protocol  out-of-the-box)
[/LIST]
 
[*] Document the minimum system requirements for successfully running this CD-based OS to work remotely
[/LIST]
Is this possable>? thanx soooo much in advance.

Probably, though a Live USB with persistence would most likely be easier than creating a custom CD image.

System-Administration-Startup Disk Creator

Make one and see if it does what you need.

---

### Post by haqking on 2011-09-09
> **dcstar said:**
> Probably, though a Live USB with persistence would most likely be easier than creating a custom CD image.

System-Administration-Startup Disk Creator

Make one and see if it does what you need.

+1

Yeah sounds about right.  here is a link to a USB with persistance.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

but as you want CD then see here

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

---

### Post by Cheesemill on 2011-09-09
Just set up Ubuntu how you want it with all of your required applications and then use [Remastersys]("http://www.geekconnection.org/remastersys/index.html") to create a Live CD of your installation.

---

### Post by 04prixgt04 on 2011-09-09
thanks for all the heads up. I am going to get started tonight

---

### Post by buttons01 on 2011-10-28
> **Cheesemill said:**
> Just set up Ubuntu how you want it with all of your required applications and then use [Remastersys]("http://www.geekconnection.org/remastersys/index.html") to create a Live CD of your installation.

I've made a bunch of these, fast and easy.  I set mine up with Dropbox first for easy file replication.  USB is better, but the LiveCDs do work.

Cheers

---

