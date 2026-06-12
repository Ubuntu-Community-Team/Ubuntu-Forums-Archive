---
title: "website help"
date: 2010-02-26
forum: General Help
---

### Post by patchido on 2010-02-26
starting off, i am not sure if this thread is suposed to go here cause i did not find any forum that specified into this, so i went general.

ok, i am not that good into writing web pages and what i actually want i believe it is so simple, but i just cant figure out how to do it.

i have this web page, [www.miercolitos.freehostia.com]("www.miercolitos.freehostia.com") it is an spredsheet saved into html, but what i want to do is for me to only upload the .xls file and for index.html to update, like, to read the file, or maybe not a spreedsheat but another method, but as i already said, i dont know much about this kind of stuff

---

### Post by johngreth on 2010-02-26
You might be able to make your own html page and embed a google doc into it. Otherwise you'll have to write your own script to display the spreadsheet.

---

### Post by PoHandle on 2010-02-26
Another option is to use PHP and MySQL to manage a spreadsheet-style page.  This method requires more work at first (requires knowledge of PHP and MySQL) but will simplify updating the information contained on the page.

PHP is great for displaying a page with dynamic content.  That is, you can write a .php file which you will not have to update often (if ever), yet the contents can change depending on variables.

More info: [http://www.php.net/](http://www.php.net/)
Great PHP tutorials: [http://www.w3schools.com/PHP/default.asp](http://www.w3schools.com/PHP/default.asp)

MySQL is database software which contains data in tables, much like a spreadsheet.  Using PHP, you can get information from a database to display on a page.  You can either edit the information within the database directly, or create a separate PHP page to allow you to access the database for updating.

More info: [http://www.mysql.com/](http://www.mysql.com/)
Great MySQL tutorials: [http://www.w3schools.com/PHP/php_mysql_intro.asp](http://www.w3schools.com/PHP/php_mysql_intro.asp)

---

### Post by eqqfooyoung on 2010-02-26
Please ignore my post

---

### Post by patchido on 2010-02-26
i dont know if any of you actually went into seeing my site, so ill ask, does php and mysql let me handle the graph? or the google doc thing?

---

### Post by johngreth on 2010-02-26
I can't access your site, but that may just be my isp's fault ( I have comcast). Any way, google docs should be able to handle a graph. It may be possible to have the graphs using php and mysql, but that would be much more difficult.

---

### Post by PoHandle on 2010-02-26
> I can't access your site, but that may just be my isp's fault ( I have comcast).
I also cannot access the site. (I have Optimum Online)  So I can't see the site.  If you're running it from a home server, make sure to enable port forwarding on your router.  Some ISP's have been known to block incoming requests on port 80, so you might have to use a non-standard port.

As for the graph, that sounds like something that would require a seperate engine/application to render.  You could try Flash, because I know that will work with dynamic graphics and can handle variables.

---

### Post by patchido on 2010-02-26
[miercolitos.freehostia.com]("miercolitos.freehostia.com")

---

### Post by sandyd on 2010-02-26
heres a nice long list....
[http://www.hotscripts.com/category/php/scripts-programs/](http://www.hotscripts.com/category/php/scripts-programs/)

personally, I would go use google apps for domains.

im not sure if its still free though.

---

### Post by johngreth on 2010-02-26
I don't know about google apps for domains, but I know if you upload a doc to google docs and click "share" you can get code to embed it into any website.

---

