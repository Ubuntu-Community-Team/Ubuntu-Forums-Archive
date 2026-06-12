---
title: "CUPS not starting"
date: 2009-09-03
forum: General Help
---

### Post by ozzyprv on 2009-09-03
For some reason CUPS does not starts. This issue started after I remove the package and reinstalled.

This is what I am getting:
```
me@box:/var/log/cups$ sudo /etc/init.d/cups restart
 * Restarting Common Unix Printing System: cupsd                                
cupsd: Child exited with status 1!
                                                                         [fail]
```

Please help.

---

### Post by sahabcse on 2009-09-03
paste the o/p of 

sudo tail -f /var/log/cups/error_log

---

### Post by ozzyprv on 2009-09-03
> **sahabcse said:**
> paste the o/p of 

sudo tail -f /var/log/cups/error_log

just blank... I tried to look into the log, I found the three files empty.

```
me:/var/log/cups$ ls -al
total 68
drwxr-xr-x  2 root root    4096 2009-09-03 07:54 .
drwxr-xr-x 14 root root    4096 2009-09-03 19:54 ..
-rw-r-----  1 root lpadmin    0 2009-09-03 07:54 access_log
-rw-r-----  1 root adm      888 2009-09-02 22:32 access_log.1.gz
-rw-r-----  1 root adm     2289 2009-09-02 00:23 access_log.2.gz
-rw-r-----  1 root adm      201 2009-08-30 18:09 access_log.3.gz
-rw-r-----  1 root adm      210 2009-08-16 07:46 access_log.4.gz
-rw-r-----  1 root adm      214 2009-08-15 07:41 access_log.5.gz
-rw-r-----  1 root adm      122 2009-08-14 07:42 access_log.6.gz
-rw-r-----  1 root adm      208 2009-08-13 08:01 access_log.7.gz
-rw-r-----  1 root lpadmin    0 2009-09-02 07:51 error_log
-rw-r-----  1 root adm      198 2009-09-01 23:38 error_log.1.gz
-rw-r-----  1 root adm      125 2009-08-31 07:38 error_log.2.gz
-rw-r-----  1 root adm      169 2009-08-30 18:09 error_log.3.gz
-rw-r-----  1 root adm      124 2009-08-29 07:37 error_log.4.gz
-rw-r-----  1 root adm      125 2009-08-28 07:44 error_log.5.gz
-rw-r-----  1 root adm      125 2009-08-27 07:55 error_log.6.gz
-rw-r-----  1 root adm      124 2009-08-26 07:56 error_log.7.gz
-rw-r-----  1 root lpadmin    0 2009-09-03 07:54 page_log
-rw-r-----  1 root adm       89 2009-09-02 00:09 page_log.1.gz

```

---

### Post by sahabcse on 2009-09-03
run the below command and complete remove the package include configuration files. Then install cups, cups-client etc

sudo apt-get purge packagename

---

