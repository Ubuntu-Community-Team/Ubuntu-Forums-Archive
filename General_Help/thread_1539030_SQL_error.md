---
title: "SQL error"
date: 2010-07-26
forum: General Help
---

### Post by aamir123 on 2010-07-26
**Hi everyone i am new in this forum . i am getting the error mentioned below. can anyone help me with that. thank you in advance .**
 
**Warning**: date() expects parameter 2 to be long, string given in **/usr/share/mysar/www/index.php** on line **43**
 
 
SQL Error 
 
ERROR on SQL query 
 
SQL query: SELECT DATE_FORMAT(date, '%W, %d %M %x') AS dateFormatted,date,MIN(date) AS minDate,MAX(date) AS maxDate,COUNT(DISTINCTROW ip) AS hosts,COUNT(DISTINCTROW usersID) AS users,COUNT(DISTINCTROW sitesID) AS sites,SUM(inCache+outCache) AS bytes,TRUNCATE(SUM(inCache)/SUM(inCache+outCache)*100,0) AS cachePercent FROM trafficSummaries GROUP BY dateFormatted ORDER BY date DESC 
 
Database error number: 144 
 
Database error message: Table './mysar/trafficSummaries' is marked as crashed and last (automatic?) repair failed 
 
Exiting...

---

### Post by dapperdanny77 on 2010-07-26
I assume you have a mysql database installed - check out [URL="http://dev.mysql.com/doc/refman/5.1/en/myisam-table-maintenance.html"]http://dev.mysql.com/doc/refman/5.1/en/myisam-table-maintenance.html
[/URL]

---

### Post by houshdaran on 2010-07-26
What programmingg language can I use to interface to MySQL(I want to write an application that stores in mySQL).

---

