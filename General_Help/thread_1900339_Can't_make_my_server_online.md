---
title: "Can't make my server online"
date: 2011-12-26
forum: General Help
---

### Post by tejli007 on 2011-12-26
hi all.
After 3 days of trying and reading on the forum cant get my server online.
 
i have installed ubuntu 10.04 
installed ssh server
installed apache msql ....
port forward 22 and 80
 
i do it from here
[[COLOR=#234786]http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-3-p3[/COLOR]]("http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-3-p3")
 
sorry for advertising
 
 
i can connect thru putty and when i type my ip in the browser i says ''its working''
but when i type my ip from mobile or from other pc cant connect.
 
 
what should i do more?
 
i have to reinstall ubuntu again couse i delete my connection.
 
any other link where can i configure step by step?
 
 
please help i really need your help

---

### Post by lisati on 2011-12-26
Is your ISP blocking port 80?

---

### Post by tejli007 on 2011-12-26
> **lisati said:**
> Is your ISP blocking port 80?
 
thanks for the reply sir.
i thing yes. before i install apache2 i was to canyouseeme.org i port 80 was open.after install apache msql ispconfig now is blocked.
 
is that normal after apache install, port 80 to be closed?
 
anyway the webmail squlmail or sqiredmail... dont know the right name(am typing from work) is blocked from isp

---

### Post by lisati on 2011-12-26
It is normal for many ISPs to block port 80. What this means is that even if you configure everything properly at your end, nobody will be access your website from outside your home network.

If you want your web site to be publicly available, you will need to either arrange with your ISP for it to be open, or to arrange to use another port.

---

### Post by tejli007 on 2011-12-26
> **lisati said:**
> If you want your web site to be publicly available, you will need to either arrange with your ISP for it to be open, or to arrange to use another port.
 
how to do it sir?any link where i can do it step by step?sorry am new in ubuntu.

---

### Post by tejli007 on 2011-12-26
> **tejli007 said:**
> how to do it sir?any link where i can do it step by step?sorry am new in ubuntu.
 
anyone please`?

---

### Post by lisati on 2011-12-27
Please do not start multiple threads for the same problem.

Is your server on the same IP address as the one you used to post this thread?

edit: using one of the crystal balls issued to forum staff, together with tools at [http://whatismyipaddress.com](http://whatismyipaddress.com), I have learned that you have a static public IP address.

---

