---
title: "Sites taking dominance"
date: 2012-04-11
forum: General Help
---

### Post by kicklinr on 2012-04-11
I have two domains coming from two providers.  

 - No-ip
 - Network solutions

Either or I have the same problem.  If both domains are activated in apache2 sooner or later one takes over the other domain.

Example:

[www.xwz.com](www.xwz.com) and [www.abc.com](www.abc.com)

after a couple days when activated xwz.com or abc.com will take over and display the content from either page.

I have done no declarations in my /etc/hosts/ just stricly stayed with apache2 configs.  

Am I missing something?

Thanks

---

### Post by alenis on 2012-04-11
I think you should configure two virtual hosts. You said you didn't change the default configuration, so I guess you don't have two propoerly defined virtualhosts.

---

### Post by kimda on 2012-04-11
I guess you are working with one external ipaddress. Have a look at name based virtual hosts. This is what you need to use when you have multiple domains on one ipadress. 

[http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html)

---

### Post by kicklinr on 2012-04-11
Followed the documentation you sent.  I just had to add the a couple pieces to my configs for each site and seems to working good for now.  

Thanks

---

