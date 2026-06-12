---
title: "Setting up file shares on ubuntu network"
date: 2011-11-30
forum: General Help
---

### Post by HBED on 2011-11-30
Morning everyone,
I'm building a small network consisting of one server and up to 50 desktop clients. It is all running on Ubuntu without a windows machine in sigh! I have everything I need pretty much sorted out but I have been struggling with setting up shared folders on the server.
I have LDAP, DNS, DHCP amongst other services installed and the final thing I need to do is to create a couple of shared storage areas on the server which users can access from any client machine. The client machines are in computer labs and are used at hot desks, so no one machine will be used by one indiviual. At the end of each week, the machines will be wiped in readiness for the next group to come in.
My question is, through all the docu I have read, most things continually refer to SAMBA, but then progress to say how you can use it to integrate you ubuntu server with a windows platform, share files and share printing abilities. But this isn't what I want to do. However, i am unsure whether SAMBA is still the correct way to do it, just omitting anything to do with windows integration. Is SAMBA the right thing i want to be using, or is there another way of carrying this out?
Thankyou for your time,
HBED

---

### Post by maverickaddicted on 2011-11-30
Yes, you can very much use SAMBA for file and printer sharing. I am currently doing it in my office, which has 10 Windows and 16 Ubuntu machines.

---

### Post by scarleo on 2011-11-30
Sounds more like a job for NFS if you ask me. As far as I understand it's way more efficient than SAMBA when you don't need windows access but there are probably, as usually, many different opinions on the matter.

---

### Post by talkingtek on 2011-12-02
here's my note I have for a while and it's still working for me.

[http://talkingtek.com/map-drive](http://talkingtek.com/map-drive)

---

### Post by HBED on 2011-12-06
> **scarleo said:**
> Sounds more like a job for NFS if you ask me. As far as I understand it's way more efficient than SAMBA when you don't need windows access but there are probably, as usually, many different opinions on the matter.
 
Hello all,
looks like NFS has done the trick.
 
Thankyou all for your help and suggestions.
 
HBED

---

