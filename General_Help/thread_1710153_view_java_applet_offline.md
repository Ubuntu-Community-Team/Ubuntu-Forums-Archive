---
title: "view java applet offline"
date: 2011-03-19
forum: General Help
---

### Post by tanyeun on 2011-03-19
I found this [site]("http://mainline.brynmawr.edu/Courses/cs206/spring2004/lafore.html") useful

I used httrack to download the entire website
but when I open the file from my computer, for example:
> $google-chrome ~/website/test/Array.html 
the java applet part only showed in blank gray, and nothing else

I could view this applet from the same browser(which is chrome)
when I linked to the internet.

any ideas how to solve this?

thx :D

---

### Post by lykeion on 2011-03-19
Java applets are made to run online. There are Java Web Start applications (JNLPs) which you can run offline, but this is not a JNLP.
And even if you're using a website downloader like httrack it'll very seldomly work with Java applets:
[http://www.httrack.com/html/faq.html#Q2b](http://www.httrack.com/html/faq.html#Q2b)

---

