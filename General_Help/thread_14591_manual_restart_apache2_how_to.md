---
title: "manual restart apache2: how to?"
date: 2005-02-08
forum: General Help
---

### Post by isaac on 2005-02-08
Hi,

   i'm new to ubuntu . I have problem knowing how to restart apache in ubuntu. Where does ubuntu put apachectl file? usually if we download and install apache2 from indivual package(directly from [www.apache.org](www.apache.org)) the location for the apachectl to start HTTP is "/usr/local/apache2/apachectl start" but in ubuntu 

where is apache located? (i need to know where to httpd.conf file located too)

how can i change the directive(apache2-default) on first login to my http?

thanks in advance =)

---

### Post by WillCooke on 2005-02-08
[QUOTE=isaac]Hi,

   i'm new to ubuntu . I have problem knowing how to restart apache in ubuntu. Where does ubuntu put apachectl file? usually if we download and install apache2 from indivual package(directly from [www.apache.org](www.apache.org)) the location for the apachectl to start HTTP is "/usr/local/apache2/apachectl start" but in ubuntu 

where is apache located? (i need to know where to httpd.conf file located too)

how can i change the directive(apache2-default) on first login to my http?

thanks in advance =)[/QUOTE]


This is all off the top of my head, so if it's wrong, sorry but it might get you started (If it is incorrect I'll come back and delete this....

To start and stop apache type>

  /etc/init.d/apache(2?) restart

You can also replace restart with start or stop

I think by default the httpd.conf is in /etc/apache and by default your HTML docs should go in /var/www

HTH,

W

---

### Post by benjamin on 2005-02-11
You can found apachectl  in:
/usr/sbin

---

### Post by benjamin on 2005-02-11
Sorry .....   /usr/sbin/apache2ctl

---

