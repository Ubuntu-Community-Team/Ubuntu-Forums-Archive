---
title: "Restrict Access to WebServer"
date: 2011-06-16
forum: General Help
---

### Post by ptmuldoon on 2011-06-16
Before I go ahead and porforward port 80 to allow access to my webserver, I was wondering if/how you can protect the access to your webserver to just specific users, etc?

Can I you have the server request a username and password for specific directories?

ie, right now I have

/var/www/index
/var/www/site1/
/var/www/site2/

I'd like to ensure that I have access to sites 1 and 2, but that the general public does not.  Basically, I have an online address book of contacts, phone numbers, etc, and do not want to go putting that out there for public display.

Thanks

---

### Post by amauk on 2011-06-17
assuming you're using Apache, here's Apache's documentation for [Authentication, Authorization and Access Control](http://httpd.apache.org/docs/2.2/howto/auth.html)

---

