---
title: "Apache won't serve up index.php"
date: 2010-01-13
forum: General Help
---

### Post by cory_ on 2010-01-13
I recently restarted my Apache server to change the max upload from 5mb to 25mb.  Once Apache restarted I tryed to go to my website via url [www.website.com](www.website.com) and a blank page with this source code:

<html> 
<body bgcolor="#FFFFFF"> 
</body> 
</html>

I also have two demo websites that I am running and when I go to there url's [www.website.com/demosite](www.website.com/demosite) apache will serve up the index.php

I didn't change anything but the max_upload in the apache2.conf and restarted.  I have no idea how to fix this problem so any suggestions would be great.

---

### Post by cory_ on 2010-01-13
Problem Solved!!!  It was found that my system created a index.html without my knowledge.  Apache first looks for html before php and serves up the index.html first.  this was preventing my website from being launched. :o

---

