---
title: "how to determine ubuntu version and upgrade php/mysql with Plesk"
date: 2010-09-24
forum: General Help
---

### Post by bcraigie on 2010-09-24
Hi,

I am trying to determine which version of Ubuntu we have installed on our Webfusion VPS in order to see how to update to specific php and mysql versions needed for installing some software.

uname -a gives this:

Linux [hostname] 2.6.18-028stab070.2 #1 SMP Tue Jul 6 14:34:09 MSD 2010 x86_64 GNU/Linux

I don't see anything that matches up to any of the Ubuntu releases.  Is there any other way to determine what we have?

We have Plesk 9.5.2 on the machine.

Certain software we need to install requires  [COLOR=darkgreen][FONT=&quot]PHP       5.2.10+ and Mysql 5.2+[/FONT][/COLOR][COLOR=black][FONT=&quot]
    but we currently have PHP 5.2.4-2ubuntu5.12 with Suhosin-Patch 0.9.6.2 and Ver 14.12 Distrib 5.0.51a

Please can someone advise how to get the required versions of php and mysql (without breaking Plesk)?  I tried editing /etc/apt/sources.list to add a new repository and using apt-get upgrade php but I probably did not add the correct repository.

Grateful for any advice.

Thanks,

Brian





[/FONT][/COLOR]

---

### Post by bcraigie on 2010-09-24
I've just found /etc/lsb-release which says it is Hardy 8.04

So, just need to find out how to upgrade php and mysql. :-)

Brian

---

### Post by bcraigie on 2010-09-27
Please can anyone help?

I need to update php and mysql to the versions I listed in my first post.  I have experience of building from source if necessary, but not sure how that would affect Plesk.

Warmest Regards,

Brian

---

