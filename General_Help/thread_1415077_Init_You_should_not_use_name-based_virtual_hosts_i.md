---
title: "Init: You should not use name-based virtual hosts in conjunction with SSL!!"
date: 2010-02-24
forum: General Help
---

### Post by milindras on 2010-02-24
Hi,
im getting a strange warning from apache:
 
[Wed Feb 24 16:33:51 2010] [warn] Init: SSL server IP/port conflict: oak.virtual-datarooms.co.uk:443 (/etc/httpd/conf.d/ssl.conf:306) vs. syndicus.virtual-datarooms.co.uk:443 (/etc/httpd/conf.d/ssl.conf:513)
[Wed Feb 24 16:33:51 2010] [warn] Init: SSL server IP/port conflict: enablesoft.virtual-datarooms.co.uk:443 (/etc/httpd/conf.d/ssl.conf:287) vs. syndicus.virtual-datarooms.co.uk:443 (/etc/httpd/conf.d/ssl.conf:513)
[Wed Feb 24 16:33:51 2010] [warn] Init: SSL server IP/port conflict: personalstorage.virtual-datarooms.co.uk:443 (/etc/httpd/conf.d/ssl.conf:268 ) vs. syndicus.virtual-datarooms.co.uk:443 (/etc/httpd/conf.d/ssl.conf:513)
[Wed Feb 24 16:33:51 2010] [warn] Init: You should not use name-based virtual hosts in conjunction with SSL!!
[Wed Feb 24 16:33:51 2010] [notice] Apache/2.2.2 (Fedora) configured -- resuming normal operations
 
 
When I looking at the log, this log looks like started week ago. im not sure why suddenly this!
 
When I search on the internet , it says name base virtual hostes not supported by SSL, But Why i didnt see this log before??
 
Thanks

---

