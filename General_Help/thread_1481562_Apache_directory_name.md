---
title: "Apache directory name"
date: 2010-05-12
forum: General Help
---

### Post by amainejr on 2010-05-12
I'm having a problem naming a subfolder in my /var/www/ directory.  I'm trying to create a directory named javascript, so I can keep a few scripts in there that I'd use frequently.  When I name it 

/var/www/javascript/test.html

I get a 404 error.  If I simply rename the javascript directory to jscript, it has not problem accessing the files contained within.  Is this a security issue or is there something wrong with my configuration?  I've got 5 other directories including images, php, upload, database, and browsertools, and have no problem accessing them in any way.  It is only when I have the javascript subdirectory that I get the 404.  Let me know the commands you want me to post, or if it's just something inherent in Apache.

---

### Post by amainejr on 2010-05-12
Nevermind, found something on google.  It's apparently a setting in a file in the conf.d subdirectory.  Anyone care to explain what this is for, or why would I need it?

/etc/apache2/conf.d/javascript-common.conf


[http://www.webmasterworld.com/apache/4063457.htm](http://www.webmasterworld.com/apache/4063457.htm)

---

