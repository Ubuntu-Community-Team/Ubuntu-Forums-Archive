---
title: "How to Install CGI for Apache2 on Ubuntu.."
date: 2011-12-16
forum: General Help
---

### Post by TT00TT on 2011-12-16
Can someone please pass me along to a tutorial for setting up CGI on Ubuntu, I have installed apache2, cgi module is installed, chmod cgi-bin dir but I still get...

[http://localhost/cgi-bin/](http://localhost/cgi-bin/)

Forbidden

You don't have permission to access /cgi-bin/ on this server.
Apache/2.2.20 (Ubuntu) Server at localhost Port 80

---

### Post by Lars Noodén on 2011-12-16
That's correct, you cannot browse the CGI directory.  You can put  a script in that directory and then enter the full URL to run it as a CGI script.  What language do you want to write your scripts in?

---

