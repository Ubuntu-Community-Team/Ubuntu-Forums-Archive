---
title: "Virtual package dependency? (squirrelmail with lighttpd)"
date: 2010-09-21
forum: General Help
---

### Post by colinmb on 2010-09-21
I'd like to use Squirrelmail with lighttpd instead of Apache, and I have lighttpd installed (which, I believe, satisfies the "httpd" virtual package.) I would expect the Squirrelmail package to find that I already have an httpd, but it wants to install Apache anyway.

What should I do to make the Squirrelmail installation see that the "httpd" requirement is already met?

--Colin

---

### Post by colinmb on 2010-10-25
Solved. The key was to manually install the php5-cgi (rather than let the squirrelmail package pull in libapache2-mod-php5, which seems to force an Apache install.) Once lighttpd, perl, and php5-cgi are installed, installing squirrelmail didn't try to bring in Apache as well.

--Colin

---

