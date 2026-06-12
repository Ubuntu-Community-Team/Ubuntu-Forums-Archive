---
title: "Cacti / rrdtool causes PHP to memory leak"
date: 2012-06-17
forum: General Help
---

### Post by UkMeterman on 2012-06-17
Hi,
I am having some problems with Ubuntu 12.04 When I install Cacti and RRDTOOL I find I run out of memory and problems with PHP blocking processes. The memory problem gets so bad the system can't fork due to lack of memory, and the problem procesess appear to be the PHP processes assocatied with Cacti Cron jobs.  I am running a dual processor P4 E6750 @2.88GHz and I have 8GB of RAM.

Has anyone tried the standard versions of Cacti RRDTOOL MySQL and PHP, and how should I debug this?

---

