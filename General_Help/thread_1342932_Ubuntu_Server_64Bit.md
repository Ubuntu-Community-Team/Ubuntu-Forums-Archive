---
title: "Ubuntu Server 64Bit"
date: 2009-12-01
forum: General Help
---

### Post by dajoeker on 2009-12-01
Hello, I am new to this and I'm sure that someone has all ready made a thread about this. I am setting a server using Ubuntu, now since Windows automatically configures DNS, do I need to install DNS server on my Ubuntu machine? I not sure if this makes sense but please give advise! Thanks :D

---

### Post by doas777 on 2009-12-01
you will have to describe your rig and network.
you haven't said anything that indicates that you need a dns server, but...

---

### Post by dajoeker on 2009-12-01
Ok, I'm setting up Ubuntu Server 9.10 with Vmware 2.0.2, I will be seeting up WinSever 03 and WinSever 08 Standard within Vmware. So, which machine should be running the DNS server and DHCP?

---

### Post by doas777 on 2009-12-01
which ever one you want. 

as an Example, I use a bind server (dns) on my internal network. it provides name res for my internal zone, and also forwards NX requests on to my ISPs servers. that way all my clients can use both internal names for local servers, and external names for ubuntuforums.org

what are you trying to accomplish with your naming scheme?

---

### Post by dajoeker on 2009-12-01
I'm in the process of virtualizing two servers, one of the servers is a primary which supplies the DNS and DHCP. Any suggestions?

---

### Post by doas777 on 2009-12-01
if you are virtualizing the servers, then I don't see any problem with just leaving the services you had on each where they were. also is the MS dns supporting a MS AD domain>? if so, then the dns is pretty closely tied to the domain, and should remain on the windows servers.

---

### Post by dajoeker on 2009-12-01
:guitar:OK! Thank you soo much! :D Very much appreciated.

---

