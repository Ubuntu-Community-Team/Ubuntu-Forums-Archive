---
title: "Squid Proxy Server Setup"
date: 2012-07-07
forum: General Help
---

### Post by hunter.allen on 2012-07-07
Hello all, 

I am looking to set up a squid server for my home network. I want to use it to speed up web browsing. The server is running ubuntu server 12.04. I don't want to block anything, I just want to cache. I'm sure this is a simple setup, but I have no idea what I'm doing... What information do I need to set up the proxy, and where do I apply it in the configuration? 

thanks, 
-Hunter A.

---

### Post by papibe on 2012-07-07
Hi hunter.allen.

Here's a very good [guide]("https://help.ubuntu.com/12.04/serverguide/squid.html").

Tell us how it goes.
Regards.

---

### Post by hunter.allen on 2012-07-07
I think the problem is the system setup... How do I set it up on the system?

---

### Post by SeijiSensei on 2012-07-07
I'll just mention that you'll only see caching benefits from squid if you're browsing from multiple computers, and those computers/users visit some sites in common.  All browsers cache downloaded objects locally.  Running a single machine behind squid basically just moves the cache from the client machine to the squid proxy.  In fact, it will actually be duplicative unless you set the browser's cache size to zero.

Install squid with "sudo apt-get install squid3".  The configuration is contained in /etc/squid3/squid.conf.

---

### Post by papibe on 2012-07-07
Take a look at these video tutorials to get an idea on what you are trying to accomplish:
[LIST]
[*][How to install and configure squid proxy server on linux ubuntu]("http://www.youtube.com/watch?v=oqZ9Lf4V444").
[*][Install & Configure Squid Proxy Server in Ubuntu - 1/3 Beginner]("http://www.youtube.com/watch?v=LnBG_LEvvVw").
[/LIST]
Tell us how it goes.
Regards.

---

