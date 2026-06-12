---
title: "Oracle Starting Problem"
date: 2010-03-25
forum: General Help
---

### Post by JohnSearle on 2010-03-25
Hey all,

I'm attempting to get Oracle 10g installed for a class assignment (which specifically requires this version of Oracle), but I cannot get it to start properly.

I have followed this guide:

[http://mikesmithers.wordpress.com/2009/12/07/installing-oracle-xe-on-ubuntu-9-10/](http://mikesmithers.wordpress.com/2009/12/07/installing-oracle-xe-on-ubuntu-9-10/)

I kept the default IP and port (guide didn't), and I set it to not start automatically (as guide did). This allowed me to connect to the Oracle homepage the first time around, but now it will not load. I get the following error: "Firefox can't establish a connection to the server at 127.0.0.1:8080."

I did run "Start Database" followed by "Go To Database Homepage" but this fails to do anything.

Are there any thoughts on what I might be doing wrong? I've taken a look online, but haven't found any relevant information yet.

Thanks,

- John

---

### Post by JohnSearle on 2010-03-25
nm... Found out that I have to log into the Oracle user to start the DB for some reason.

---

### Post by saulwebl on 2011-01-10
> **JohnSearle said:**
> Hey all,I'm attempting to get Oracle 10g installed for a class assignment (which specifically requires this [[COLOR=#000000]version[/COLOR]](http://www.changeformat.net/change-dat-format/change-dat-to-blackberry.html) of Oracle), but I cannot get it to start properly.I have followed this guide:[http://mikesmithers.wordpress.com/20...n-ubuntu-9-10/](http://mikesmithers.wordpress.com/2009/12/07/installing-oracle-xe-on-ubuntu-9-10/)I kept the default IP and port (guide didn't), and I set it to not start automatically (as guide did). This allowed me to connect to the Oracle homepage the first time around, but now it will not load. I get the following error: "Firefox can't establish a connection to the server at 127.0.0.1:8080."I did run "Start Database" followed by "Go To Database Homepage" but this fails to do anything.Are there any thoughts on what I might be doing wrong? I've taken a look online, but haven't found any relevant information yet.Thanks,- JohnThe information is nice, but it has nothing to do with my issue, Thanks very much! Who can give an answer?

---

### Post by JohnSearle on 2011-01-10
> **saulwebl said:**
> The information is nice, but it has nothing to do with my issue, Thanks very much! Who can give an answer?

An answer to what? You didn't ask a question, and I started this thread several months ago.

The answer to my problem was that the Oracle DB requires that you log in under the Oracle username that is created by the DB installation and start the server there. Once you start the server, you can log back into your regular username to access it.

---

### Post by JohnSearle on 2011-01-10
...

---

