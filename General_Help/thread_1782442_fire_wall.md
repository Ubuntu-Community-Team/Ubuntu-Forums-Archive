---
title: "fire wall"
date: 2011-06-14
forum: General Help
---

### Post by K4NEB on 2011-06-14
does ubuntu have a firewall?

just wondered how safe i am when im using my credit card online from external intruders onto my computer.

i know linux is pretty good for virus's but there are some out there.

what about anti virus?

thankyou everyone if you give mne some answers

---

### Post by wildmanne39 on 2011-06-14
> **K4NEB said:**
> does ubuntu have a firewall?

just wondered how safe i am when im using my credit card online from external intruders onto my computer.

i know linux is pretty good for virus's but there are some out there.

what about anti virus?

thankyou everyone if you give mne some answersHi, you can use firestarter it is in the software center.

---

### Post by bodhi.zazen on 2011-06-14
> **wildmanne39 said:**
> Hi, you can use firestarter it is in the software center.

Firestarter is outdated and no longer maintained.

ufw is installed by default, and if you want a graphical interface , use gufw.

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

Or, better, learn iptables =)

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by lykwydchykyn on 2011-06-14
> **K4NEB said:**
> does ubuntu have a firewall?

just wondered how safe i am when im using my credit card online from external intruders onto my computer.

i know linux is pretty good for virus's but there are some out there.

what about anti virus?

thankyou everyone if you give mne some answers

If your concern is using your credit card online, neither a firewall nor an antivirus will really address that.  When you use a credit card online, no matter what the OS is:

 - Make sure the site and it's payment service are reputable
 - Make sure they are encrypting the entire transaction: the URL should begin with "https"
 - If you get any errors about the website's certificate, DON'T PROCEED
 - Make sure your browser is not caching any credit card information.  Best procedure is to use the browser's tools to clear all form data after making a purchase.  I believe the latest firefox tries to determine if you are entering a credit card number and asks you if you want to save it or not (say no).

---

### Post by wildmanne39 on 2011-06-14
Hi, thank you bodhi.zazen I did not know that it was outdated, I appreciate the information.

---

