---
title: "VBox guest cannot access internet"
date: 2010-08-27
forum: General Help
---

### Post by t0p on 2010-08-27
I have a virtual XP as guest in VirtualBox on a computer running Hardy.  I used to be able to access the internet from the virtual XP, using Internet Explorer or Google Chrome with no problem - it just used the Ubuntu host's connection, whch it seemed to see as a "NAT Adapter".

It still sees this NAT connection - if I hover the pointer over the Network icon in VBox it says "Adapter 1 (NAT): cable connected".  And if I use Firefox from the host OS, it connects just fine.

Why can the virtual XP no longer access the internet?  How can I fix this?

---

### Post by mendhak on 2010-08-27
You'll first want to check the connection settings in those browsers - any proxy servers specified that you didn't want to leave in?

Does a ping work from the guest OS?  Can you ping google.com, for example?

---

