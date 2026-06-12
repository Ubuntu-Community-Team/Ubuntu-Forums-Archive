---
title: "How tomcat log rollover works?"
date: 2009-08-04
forum: General Help
---

### Post by kodalisrikanth on 2009-08-04
Hi,

I got a general question. How the apache tomcat organizes its log files? What i heard is, if the log file is 10MB, then it will copy the catalina.out to catalina1.out and removes catalina.out.

And tomcat will create new catalina.out file as log file. Is there any way to track the name of the backup files in which the tomcat is storing the catalina.out every time?




Thanks,
Srikanth Kodali.

---

### Post by cariboo on 2009-08-04
If you have logrotate installed, the logs will be rotated daily, with the first rotated log call log.log.0 and the rest of the older logs get tared eg: log.log.1.gz

---

