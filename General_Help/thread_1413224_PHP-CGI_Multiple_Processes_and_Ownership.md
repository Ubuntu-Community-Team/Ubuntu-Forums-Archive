---
title: "PHP-CGI Multiple Processes and Ownership"
date: 2010-02-22
forum: General Help
---

### Post by sicpsnake on 2010-02-22
Hello. As you can see in the screenshot, PHP-CGI is running multiple processes. This irritates me, as I am a bit of a freak when it comes to these sort of things. Is there anyway I can make PHP-CGI run in one process instead of several?

Also, how can I change the ownership of the PHP-CGI process? I have already tried to chown /usr/bin/php-cgi to root, but nothing happens. Thank you for viewing this.

---

### Post by kidders on 2010-02-23
Hi there,

> **sicpsnake said:**
> Is there anyway I can make PHP-CGI run in one process instead of several?There are very few situations where that would be a good idea ... it'd cripple your server's ability to handle concurrent requests. You haven't said much about your configuration, but it looks like you might be using lighttpd/fastcgi, so you *could* get the process count down to two by setting fastcgi's max-procs parameter to 1, afaik. Normally, people only alter these values on extremely busy servers, or servers with weird configurations that react poorly to concurrency.

> **sicpsnake said:**
> I have already tried to chown /usr/bin/php-cgi to rootSurely root should already have owned that binary? :confused: In any case, the owner of an executable file doesn't have any effect on the owners of processes it starts.

Running php-cgi as root is something you *certainly* shouldn't do. To answer your question, fastcgi should have uid/gid configuration options which you could set to 0, but I wouldn't even consider doing so, tbh.

Just FYI, the changes you've outlined would be pretty unstable ... even dangerous. You shouldn't make either of them without good reason.

---

### Post by sicpsnake on 2010-02-24
Thank you. I totally forgot about fcgi's max-proc. It helped. :)

---

