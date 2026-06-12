---
title: "problem stopping lighttpd"
date: 2009-12-14
forum: General Help
---

### Post by bilal_jan on 2009-12-14
Hello everyone i am facing problem in stopping lighttpd
when i issue following command
> 
[inx-bilal@maria ~]$ /etc/init.d/lighttpd stop
Stopping lighttpd:                                         [FAILED]

Back at /var/log/lighttpd/error.log i am getting following error
> 
-> (log.c.172) server started 
-> (mod_fastcgi.c.1087) the fastcgi-backend /u/agesage/trac/release/lib/python2.5/site-packages/Trac-0.11.1-py2.5.egg/trac/web/fcgi_frontend.py failed to start: 
-> (mod_fastcgi.c.1091) child exited with status 1 /u/agesage/trac/release/lib/python2.5/site-packages/Trac-0.11.1-py2.5.egg/trac/web/fcgi_frontend.py 
-> (mod_fastcgi.c.1094) If you're trying to run your app as a FastCGI backend, make sure you're using the FastCGI-enabled version.
If this is PHP on Gentoo, add 'fastcgi' to the USE flags. 
-> (mod_fastcgi.c.1398) [ERROR]: spawning fcgi failed. 
-> (server.c.928) Configuration of plugins failed. Going down.

i have Trac-0.11.1 and python 2.5
my lighttpd.conf that deals with fastcgi support for trac is 
> 
#var.fcgi_binary="/usr/bin/python /path/to/fcgi_frontend.py" # 0.11 if installed with easy_setup, it is inside the egg directory
var.fcgi_binary="/u/agesage/trac/release/lib/python2.5/site-packages/Trac-0.11.1-py2.5.egg/trac/web/fcgi_frontend.py"
#var.fcgi_binary="/path/to/cgi-bin/trac.fcgi" # 0.10 name of prior fcgi executable
fastcgi.server = ("/trac" =>
                   ("trac" =>
                     ("socket" => "/tmp/trac-fastcgi.sock",
                      "bin-path" => fcgi_binary,
                      "check-local" => "disable",
                      "bin-environment" => ("TRAC_ENV" => "/u/agesage/trac/instance/tracd.8855/db")
                     )
                   )
                 )

i have searched alot but couldnt able to get answer for that.

---

### Post by Wardje on 2009-12-14
```
sudo /etc/init.d/lighttpd stop
```

?


Edit: reading more through the error you get, you are sure it starts up, right? Seems a bit fishy, check if it appears:
```
ps -e | grep lighttpd
```

---

### Post by bilal_jan on 2009-12-16
executing **ps -e | grep lighttpd** displays nothing
> 
[root@maria inx-bilal]# ps -e | grep lighttpd
[root@maria inx-bilal]# 

lighttpd do starts up
> 
[root@maria inx-bilal]# sudo /etc/init.d/lighttpd start
Starting lighttpd:                                         [  OK  ]
[root@maria inx-bilal]# 

> 
[root@maria inx-bilal]# sudo /etc/init.d/lighttpd restart
Stopping lighttpd:                                         [FAILED]
Starting lighttpd:                                         [  OK  ]
[root@maria inx-bilal]# 


---

### Post by Wardje on 2009-12-16
Well then I am to assume that
a. lighttpd starts up correctly
b. When loading the plugins (fastcgi to be specific), something goes wrong and lighttpd shuts down (as shown in the error log).
c. When you try to issue a stop command, it fails since lighttpd already went down

So basically, you'll have to dig deeper into why the fastcgi part fails. Which is something I'm afraid I cant help you with.

---

### Post by bilal_jan on 2009-12-18
thanks Wardje for your support.
i am looking for someone to respond to that!!!

---

