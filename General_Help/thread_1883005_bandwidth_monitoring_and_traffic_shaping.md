---
title: "bandwidth monitoring and traffic shaping"
date: 2011-11-18
forum: General Help
---

### Post by linux44 on 2011-11-18
Hello All,
 
I am looking into a solution and software whereby I can redirect all network traffics through it and have a good control over who is using how much bandwidth and monitor the daily usage
 
what are the available softwares that you recommand which has a flexibility and scalibility
 
I am not looking for something very complex but rather professional and maybe easy to implement. for example i rather use postfix as opposed to sendmail
 
any ideas?

---

### Post by blueridgedog on 2011-11-18
I recommend you research iptables, specifically the INET_IN and INET_OUT feature.

Here is a simple article:

[http://www.cyberciti.biz/faq/linux-configuring-ip-traffic-accounting/](http://www.cyberciti.biz/faq/linux-configuring-ip-traffic-accounting/)

If you Google iptables and bandwidth monitoring you will see several projects that attempt to do this with additional code or other methods.  

Iptables is a bit complex, but no so much so that it can not be mastered.  You can find examples for almost any task you want to undertake, but it will assume you have a solid understanding of networking (physical and logical).

---

