---
title: "output/run python script via http"
date: 2012-04-24
forum: General Help
---

### Post by ahso4271 on 2012-04-24
Hi
how to run a pyhton script on an apache?
Thanks

---

### Post by sanderj on 2012-04-24
> **ahso4271 said:**
> Hi
how to run a pyhton script on an apache?
Thanks

Enable CGI-BIN. See [http://httpd.apache.org/docs/2.0/howto/cgi.html](http://httpd.apache.org/docs/2.0/howto/cgi.html)

---

### Post by LemursDontExist on 2012-04-25
I would recommend [WSGI]("http://en.wikipedia.org/wiki/Web_Server_Gateway_Interface") instead.  [Here's]("http://ubuntuforums.org/showthread.php?t=833766") a tutorial to install/configure it, and [here's]("http://en.wikipedia.org/wiki/Web_Server_Gateway_Interface#Example_application") a simple example script.

WSGI is hugely more efficient than the old-style CGI interface which forks a new process for every request.  If you ever get any serious traffic, it's worth looking into.

---

