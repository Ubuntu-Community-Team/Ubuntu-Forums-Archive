---
title: "Zabbix installation on Ubuntu 9.04 Desktop Edition"
date: 2009-08-19
forum: General Help
---

### Post by himanwish on 2009-08-19
Hi guys,
 
I'm new to linux and I have to install Zabbix on Ubuntu 9.04 Desktop edition.
 
I've installed apache 2, PHP, MySQL and finally Zabbix.
 
But, in Zabbix frontend it says "Zabbix server is running - No".
 
How can I rectify this issue?
 
Thanks.

---

### Post by Jaeius on 2009-10-13
i'm also planning to install zabbix,..


maybe we could help each other..

i'll update you regarding my installation..

---

### Post by Jaeius on 2009-10-14
ok. got mine working...


how do you add elements to the map?

having trouble with the icon part.. how do i fix this? :confused:

error:

[LIST]
[*] Warning. Field [iconid_off] is mandatory
[*] Warning. Field [iconid_on] is mandatory
[*] Warning. Field [iconid_unknown] is mandatory
[*] Warning. Field [iconid_disabled] is mandatory
[/LIST]

---

### Post by Jaeius on 2009-11-05
fixed the problem by uploading the default zabbix icons for mysql


mysql -u root -p zabbix < /home/zabbix/zabbix-1.6.4/create/data/images_mysql.sql

---

