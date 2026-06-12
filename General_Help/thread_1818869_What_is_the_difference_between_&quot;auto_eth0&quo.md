---
title: "What is the difference between &quot;auto eth0&quot; and &quot;Wired connection 1&quot;"
date: 2011-08-05
forum: General Help
---

### Post by bigred1 on 2011-08-05
Using Lucid.

Both "auto eth0" and "Wired connection 1" appear in my network app.   See screenshot. I only have one Ethernet card.  

is the latter just a rename of the former?  I thought so, but the "Wired connection 1" seems to be more reliable than "auto eth0"

---

### Post by bodhi.zazen on 2011-08-05
There are two methods of configuring your interfaces, one in /etc/network/interfaces (auto eth0) and network manager (Wired Connection One).

Two names for the same interface configures by two different processes.

---

### Post by bigred1 on 2011-08-05
> **bodhi.zazen said:**
> Two names for the same interface configures by two different processes.

Thank you. So since they are the same thing, can/should I delete one.

---

### Post by bodhi.zazen on 2011-08-05
> **bigred1 said:**
> Thank you. So since they are the same thing, can/should I delete one.

Probably, but, it is not broken, why fix it ?

---

### Post by grahammechanical on 2011-08-05
From my testing of 11.10 Alpha 2, I would like to add that come the release of 11.10 in October you might find the Wired connection is the expression that replaces Auto eth. I would agree with this change if it actually takes place. It is a more understandable expression to new users.

Regards.

---

### Post by tech.biztech on 2011-08-06
> **bigred1 said:**
> Using Lucid.

Both "auto eth0" and "Wired connection 1" appear in my network app.   See screenshot. I only have one Ethernet card.  

is the latter just a rename of the former?  I thought so, but the "Wired connection 1" seems to be more reliable than "auto eth0"

Currently I am using "auto eth0" with ubuntu 8.10 and I had never find any kind of problem and I think it good with other version.

---

