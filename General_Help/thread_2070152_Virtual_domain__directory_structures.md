---
title: "Virtual domain  directory structures"
date: 2012-10-12
forum: General Help
---

### Post by ELMIT on 2012-10-12
I got a new server with the IP 11.22.33.44
I installed appache and get with [http://11.22.33.44](http://11.22.33.44) "It works!" - this index.html is /var/www/index.html

Next I set up virtual domains and used the Document root /var/www/abc.com and /var/www/def.info
I added the IP address of abc.com and def.info into the host file, which is 11.22.33.44
abc.com is a static web site.
def.info is a blog which uses a .htaccess to redirect subdirectories as different blogs
(It seems that this all gets confused, like me!!!)

[http://11.22.33.44](http://11.22.33.44) shows the index.html "It works"
[http://abc.com](http://abc.com)  shows a new subdomain
[http://def.info](http://def.info) shows the index.html "It works"

What am I doing wrong?

---

### Post by ELMIT on 2012-10-12
I found my mistake:
I used in /etc/hosts 
11.22.33.44  def.info

but it should be:
127.0.0.1   def.info

(Thanks for listening, ...)

---

