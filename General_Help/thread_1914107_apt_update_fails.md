---
title: "apt update fails"
date: 2012-01-23
forum: General Help
---

### Post by reza.adinata on 2012-01-23
Hi all,

I have a unique problem in my virtual machine, ubuntu 10.10. I tried to do apt-get update, but it tries to reach a certain private address that I do not recognize (192.168.2.1) instead of the repo. 

Tried ping to google.com , it works (get icmp reply). However, when I tried to open google.com via browser, it does not work. Check port 80, it opens.
Check the gateway and route, it points to the correct address.

I am confused, what is the problem might be, how can I update the apt?:confused:

Thank you

---

### Post by maverickaddicted on 2012-01-24
Have you configured the network on the Ubuntu?

---

### Post by reza.adinata on 2012-01-24
yes.

I can ping other website.. means i am already connected to the network . Or?

---

### Post by raja.genupula on 2012-01-24
> **reza.adinata said:**
> Hi all,

I have a unique problem in my virtual machine, ubuntu 10.10. I tried to do apt-get update, but it tries to reach a certain private address that I do not recognize (192.168.2.1) instead of the repo. 

Tried ping to google.com , it works (get icmp reply). However, when I tried to open google.com via browser, it does not work. Check port 80, it opens.
Check the gateway and route, it points to the correct address.

I am confused, what is the problem might be, how can I update the apt?:confused:

Thank you

Hi change your update server to some other best mirror and then try again .For changing open your settings of update manager .

---

