---
title: "Web server, VirtualHost and users permissions"
date: 2011-01-17
forum: General Help
---

### Post by JackTheKnife on 2011-01-17
So far I have done:
- added new user "booboo", which has own public_html folder 
- Apache has loaded config file for VirtualHost with DocumentRoot pointed to the proper folder

Everything was OK (default index.html file shows up) till user decided to upload own content. Folder and files have set permissions to "booboo" as owner and www-data as group. When I will set everything to www-data then user "booboo" can't edit own files, but when he will upload new files to the public_html folder those files are not available for web access.

What I have done wrong and where? Thanks.

---

### Post by JackTheKnife on 2011-01-18
Bump

---

### Post by JackTheKnife on 2011-01-18
Get it solved:

- addedd "booboo" to the www-data group
- set local_umask 022 for vsftpd

---

