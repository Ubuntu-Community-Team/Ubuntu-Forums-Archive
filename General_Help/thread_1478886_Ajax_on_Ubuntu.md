---
title: "Ajax on Ubuntu?"
date: 2010-05-10
forum: General Help
---

### Post by ajwei810192 on 2010-05-10
Hi, 

  I have been investigating some other web development strategies, and l started reading about Ajax and wanted to try some myself. I took the code from [http://www.w3schools.com/php/php_ajax_rss_reader.asp](http://www.w3schools.com/php/php_ajax_rss_reader.asp), and copied it to my editor in gEdit in my var/www folder, and then opened up the page. 

  Seems nothing is missing, but function-wise, I cannot get it to display anything when I tried to change the drop down menu. by dragging it with my mouse. 

Do I need to do anything special with my LAMP server to let Ajax run? 

Thanks for your help.

---

### Post by WorMzy on 2010-05-10
No, AJAX is all client side as, as the name suggests, it's done using Javascript.

---

### Post by wojox on 2010-05-10
So you should have two pages in /var/www

A html page and a php page called getrss.php

---

### Post by WorMzy on 2010-05-10
I see what the problem is. In the html file, the function being called by the select box's onchange is called "showRSS", but the function written in javascript is called "showResult". Gotta say, that's pretty sloppy by w3schools, they're usually better than that. =/

---

### Post by ajwei810192 on 2010-05-10
Silly me, thanks for pointing that out. Now it is working.

---

