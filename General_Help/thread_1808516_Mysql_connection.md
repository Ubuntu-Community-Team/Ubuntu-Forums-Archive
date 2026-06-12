---
title: "Mysql connection"
date: 2011-07-20
forum: General Help
---

### Post by Crome on 2011-07-20
Don't know if here is the right place to ask this question. I am running Ubuntu 10 server. Noticed some times connection to the database is very, very slow. I now realized that when there is no internet the database slows to a crawl then works fine when the internet returns. Can anyone tell me what is happening here. Would appreciate any help. Thanks.

---

### Post by SeijiSensei on 2011-07-20
Where's the database located?  On the local machine or on a network server?  What IP address are you using to reference the server?

---

### Post by Crome on 2011-07-22
The server is local, in our LAN , that is why I am puzzled sorry took so long to respond.

---

### Post by ingramproductions on 2011-07-22
So you have Ubuntu 10 on your LAN that runs mysql. You access your database from the same LAN, and sometimes it is slow, especially while the internet is down...
hmmm...

Sounds like you are having some network issues on your LAN. Doesn't sound related to Ubuntu. Maybe you should check the logs on your gateway or switches...

---

### Post by Habitual on 2011-07-23
When the 'net is slow, does mysql -h ipa.ddr.ess -u$user -p$password make any difference?

---

### Post by Crome on 2011-07-24
I can access the server ok and ssh to it even run webmin fine at that time. Only mysql slow to a crawl when there is no internet. Tested it on a 2003 server machine and that does not happen.

---

### Post by erittaf on 2011-10-29
> **Crome said:**
> Don't know if here is the right place to ask this question. I am running Ubuntu 10 server. Noticed some times connection to the database is very, very slow. I now realized that when there is no internet the database slows to a crawl then works fine when the internet returns. Can anyone tell me what is happening here. Would appreciate any help. Thanks.
I recently had the same issue.  It appears the SQL processes were trying to hit DNS to verify host names...  I added the relevant machines to the hosts file and now everything works normally.  (I am only dealing with a MythTV frontend and backend.)  If you are dealing with a larger network where hosts-filing all the affected computers is impractical you may want to use the --skip-name-resolve option in mysql.  Unfortunately you may have to comb your database and make sure there are no entries that use the host name of any given machine.  Really I think the better solution for a larger network is to host a proxy DNS somewhere on your LAN, specify all the internal DNS you need and then have it go out to your ISP for anything it doesn't know about.

Some reference links:
SQL DNS usage:
[http://dev.mysql.com/doc/refman/5.0/en/dns.html](http://dev.mysql.com/doc/refman/5.0/en/dns.html)

ubuntu hosts file:
[http://linuxservertutorials.blogspot.com/2008/11/ubuntu-hosts-file.html](http://linuxservertutorials.blogspot.com/2008/11/ubuntu-hosts-file.html)

Hope this helps someone out there
~E

---

