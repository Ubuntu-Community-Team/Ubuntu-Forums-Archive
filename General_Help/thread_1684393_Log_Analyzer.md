---
title: "Log Analyzer"
date: 2011-02-09
forum: General Help
---

### Post by sj1410 on 2011-02-09
Hi,

There are lot of log files in /var/log. much of them are very important but hard to understand like kernel.log, dmesg, etc... Is there some log analyzer available ( commercial or free ) which can analyze  this files and present in an understandable form.


something which can help in diagnosing a kernel crash, errors, etc...

---

### Post by [Snc] on 2011-02-09
> **sj1410 said:**
> Hi,

There are lot of log files in /var/log. much of them are very important but hard to understand like kernel.log, dmesg, etc... Is there some log analyzer available ( commercial or free ) which can analyze  this files and present in an understandable form.


something which can help in diagnosing a kernel crash, errors, etc...

You have the log viewer already installed.

System -> Administration -> Log File Viewer

Then you can read all the logs in one place. If you have specific problems, the forum members will help you.

---

### Post by anglican on 2011-02-09
> **sj1410 said:**
> Hi,

There are lot of log files in /var/log. much of them are very important but hard to understand like kernel.log, dmesg, etc... Is there some log analyzer available ( commercial or free ) which can analyze  this files and present in an understandable form.


something which can help in diagnosing a kernel crash, errors, etc...[logwatch]("http://sourceforge.net/projects/logwatch/files/") provides reasonable summary reports.

H

---

### Post by [Snc] on 2011-02-09
> **anglican said:**
> [logwatch]("http://http://sourceforge.net/projects/logwatch/files/") provides reasonable summary reports.

H

the link says "server not found" .... [This]("http://sourceforge.net/projects/logwatch/files/") is the correct link

---

### Post by Wtower on 2011-02-09
I heavily rely on **logcheck** (software center) for the security of my servers along with some custom scripts based on grep.

---

