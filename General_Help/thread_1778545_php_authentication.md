---
title: "php authentication"
date: 2011-06-09
forum: General Help
---

### Post by wonave on 2011-06-09
Hi guys!
I want to write a script that keeps "grepping" strings from the Main page of the Linksys PAP2T every 30 seconds.
It seems to be simple:
1- lynx -auth=user:password URL
2- grep the strings
3- process them

the problem is that the page is writed in PHP and Lynx does not clear    the authentication credentials with a 401 server response!

w3m works.. but I don't know how to set the autologin and how to export the page to a  text.

With firefox.. I can set the home page as [http://user:password@URL](http://user:password@URL) but it ask if it can continue before sending the data.. how can I force it and how can I obtain a text from it?I don't know.

Do you have any solution?

thanks!

---

### Post by wonave on 2011-06-10
up

---

