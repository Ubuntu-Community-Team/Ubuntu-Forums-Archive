---
title: "server &amp; inventory for eBay user"
date: 2012-04-27
forum: General Help
---

### Post by teeleef on 2012-04-27
Hi all, 

One of my friends went over to Ubuntu a few years back and has not regretted it once, anyway their Daughter is doing very well selling small household stuff on eBay.
She bought a some website to advertise her business.  On a recent visit I casually suggested it would be great if she could have a server at home hosting her website and managing her business inventory etc?

It was just a suggestion as she seems keen on Linux in general. 

I recently got an email from her claiming she is very interested in pursuing this....

Has anyone out there succeeded in such a venture?  

Any suggestions would be much appreciated.  She is prepared to pay for this functionality and seems keen on the 'open source' way to go.

Regards,


Teeleef

---

### Post by Monotoko on 2012-04-27
A home server on a residential connection generally isn't reliable enough to run a server on, the throughput just isn't there for more than a few people at a time.

However, if she is interesting in administering her own server, there are plenty of VPS providers who give bare-bones servers to configure as you wish. If you PM me I will give you a few suggestions, I won't post them here as I don't want people to think I'm spamming :)

---

### Post by techsupport on 2012-04-27
> **teeleef said:**
> Hi all, 

One of my friends went over to Ubuntu a few years back and has not regretted it once, anyway their Daughter is doing very well selling small household stuff on eBay.
She bought a some website to advertise her business.  On a recent visit I casually suggested it would be great if she could have a server at home hosting her website and managing her business inventory etc?

It was just a suggestion as she seems keen on Linux in general. 

I recently got an email from her claiming she is very interested in pursuing this....

Has anyone out there succeeded in such a venture?  

Any suggestions would be much appreciated.  She is prepared to pay for this functionality and seems keen on the 'open source' way to go.

Regards,


Teeleef

Here you go:

[http://www.ubuntu.com/business/services/overview](http://www.ubuntu.com/business/services/overview)

:popcorn:

---

### Post by josephmills on 2012-04-27
Is this going to be deployed via cloud ? what type of cms is she using at this time ? what are the things that she needs ? thanks
wew is a link to ubuntu advantage program 
[http://ubuntustreetteam.tk/wp-content/uploads/UA.pdf](http://ubuntustreetteam.tk/wp-content/uploads/UA.pdf)

---

### Post by teeleef on 2012-04-27
Thanks for the replies..... I will try to find out what setup she has at present and report back.

I tend to agree with the throughput concerns Monotoko.  I think she was hoping to invest in a full Linux run package which she perceived (right or wrong) would be more reliable and competitively priced.

I'll report back.


Teeleef

---

### Post by Monotoko on 2012-04-27
Servers and home connections are a disaster waiting to happen. Nothing to do with the OS involved.

The connection will probably struggle more than the server, she may also get frustrated with the slower internet speed since the majority of the little resources a home connection has will be on the server.

As a say, a bare bones VPS (one that you can log into and configure using SSH) sounds like it would be best.

---

### Post by pbrane on 2012-04-27
I don't know where she is located, but in general a dedicated connection to a home can be done. They can be expensive though.

However as already pointed out, a standard residential broadband connection will probably not be able to sustain the bandwidth required. Theses connections are asymmetric so the effective bandwidth will be the lower of the two, usually the upstream side. Being dynamic bandwidth even that speed will not be sustainable.

There are other considerations as well, power, power backup, security.

---

### Post by Xanko on 2012-04-27
I use linode.com to setup a business reliable Ubuntu server for web hosting.

---

### Post by Habitual on 2012-04-27
> **Monotoko said:**
> Servers and home connections are a disaster waiting to happen. Nothing to do with the OS involved.

Amen.

---

