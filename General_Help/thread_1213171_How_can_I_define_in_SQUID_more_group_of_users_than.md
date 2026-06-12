---
title: "How can I define in SQUID more group of users than one"
date: 2009-07-14
forum: General Help
---

### Post by polo23 on 2009-07-14
Hi I have problem with SQUID. SQUID works perfect but I have defined file with forbidden web pages(acl forbidden url_regex -i "/etc/squid/forbidden"). Then I have defined file with users(only one - student) and passwords 
touch /etc/squid/squid_passwd.
htpasswd /etc/squid/squid_passwd student.

Ïn squid.conf  I have
 auth_param basic program    /usr/lib/squid/ncsa_auth      /etc/squid/squid_passwd
acl ncsa_users proxy_auth REQUIRED
http_access deny forbidden
http_access allow ncsa_users.
It works fine...

I have only one group of users and my question is: How create next group of users. My imagine is following:
First group will have forbidden  access to  (for example) FILE(with forbidden web pages).
Second group  will have forbidden  access to  (for example) FILE2 (with forbidden web pages).

Please help me I am agonized. I found whole day on google but I didnt any instruction for this. Thank you very much for each idea.
Regards Polo23

---

