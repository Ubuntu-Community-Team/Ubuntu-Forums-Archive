---
title: "Moblock grants unwated access (for me)"
date: 2010-03-30
forum: General Help
---

### Post by OrdoAbChao on 2010-03-30
Hello.
I was sick and tired with windows and it's viruses and decided some time ago to use ubuntu. I love Linux based operating systems.

Now , I installed blockcontrol-moblock-mobloquer and it's working real well except one problem.

Everytime I start my computer , mobloquer automatically grants access to this DNS server. I really want to get rid of any access to my computer and internet connection.

This is the log for my mobloquer:

---

2010-03-30 18:46:13 EEST Begin: blockcontrol start
Inserting iptables ...
Allowing outbound traffic to DNS server 193.231.189.19   ...done.
Allowing forwarded traffic to DNS server 193.231.189.19   ...done.
Allowing loopback traffic   ...done.
   ...done.
Starting moblock ...   ...done.
Starting blockcontrol.wd ...   ...done.
2010-03-30 18:46:13 EEST End: blockcontrol start

---

How can I remove this "allowing"?

Pls help.

Thank u.

---

### Post by jre on 2010-04-01
Set ```
WHITE_LOCAL="0"
``` in /etc/blockcontrol/blockcontrol.conf and restart blockcontrol.


BTW, this DNS whitelisting is only for OUTgoing traffic (traffic that originates on your machine).

You'll find the whole set of configuration options in /usr/lib/blockcontrol/blockcontrol.defaults.

Have fun

---

