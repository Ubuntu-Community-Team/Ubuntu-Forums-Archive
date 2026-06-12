---
title: "Help with missing files"
date: 2006-04-11
forum: General Help
---

### Post by Linux-Newbe on 2006-04-11
Hi I am trying to compile Zabbix and get the following message

configure: error: Invalid MySQL directory - unable to find mysql.h

I have had a look and it appears this is related to mysql-dev or mysql-devel but I can find this to install from the synaptic package manager

Can anyone please point me in the right direction

Thanks

---

### Post by dcstar on 2006-04-11
[QUOTE=Linux-Newbe]Hi I am trying to compile Zabbix and get the following message

configure: error: Invalid MySQL directory - unable to find mysql.h

I have had a look and it appears this is related to mysql-dev or mysql-devel but I can find this to install from the synaptic package manager

Can anyone please point me in the right direction

Thanks[/QUOTE]
Try the libmysql-dev packages.

---

### Post by Linux-Newbe on 2006-04-12
Thanks I have got past that issue. I now need to start Zabbix_server as zabbix user. But can not seem to use sudo to do this.

---

### Post by lifeempowered.com on 2006-06-29
[QUOTE=Linux-Newbe]Thanks I have got past that issue. I now need to start Zabbix_server as zabbix user. But can not seem to use sudo to do this.[/QUOTE]

As Zabbix says, you need to create a separete user for this...It's not a good idea to run it as root.

---

### Post by RichJacot on 2006-08-11
Just to help other people (maybe)...  I needed to install libmysql++-dev to get mysql.h

---

