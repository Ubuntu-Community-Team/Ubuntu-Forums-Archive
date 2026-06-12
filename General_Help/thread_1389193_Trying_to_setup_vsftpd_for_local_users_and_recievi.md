---
title: "Trying to setup vsftpd for local users and recieving 421 error at login"
date: 2010-01-24
forum: General Help
---

### Post by rpark on 2010-01-24
I have vsftpd running with anonymous users disabled and local users enabled.
 
When I try to test it by logging in with a local users account I recieve the following error message:
 
421 Service not available, remote server has closed connection
Login failed.
No control connection for command: No such file or directory
 
 
If I edit the vsftpd.conf file to re-enable anonymous users I can login just fine, but unfortunately so can anyone else...

---

