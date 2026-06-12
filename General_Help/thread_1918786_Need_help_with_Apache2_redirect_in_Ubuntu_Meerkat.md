---
title: "Need help with Apache2 redirect in Ubuntu Meerkat"
date: 2012-02-01
forum: General Help
---

### Post by Shftz on 2012-02-01
Ubuntu 10.10
Apache2 v2.2.16
 
I currently have two domains (domain1 and domain2).  Domain1 one has a vhost setup to land on the correct home page and everything works fine.  The second domain (domain2) has a seperate vhost and the landing page for domain2 needs to be [www.domain1.com/products/foo.php]("http://www.domain1.com/products/foo.php").  I setup a redirect in domain2's vhost that points all [www.domain2.com]("http://www.domain2.com") to [www.domain1.com/products/foo.php]("http://www.domain1.com/products/foo.php").  This works fine and all [www.domain2.com]("http://www.domain2.com") traffic drops right onto [www.domain1.com/products/foo.php.......HOWEVER]("http://www.domain1.com/products/foo.php.......HOWEVER") the problem I'm running into is that if someone does a google search and tries to click a link that has a sub-directory such as [www.domain2.com/contact.php]("http://www.domain2.com/contact.php") the redirect turns the URL into [www.domain1.com/products/foo.phpcontact.php]("http://www.domain1.com/products/foo.phpcontact.php") and renders the URL to a 404. The entire URL is ammended with what was in the redirect.
My question is how can I setup a redirect with the correct reg ex to get this to work properly.  Any help would be greatly appreciated.

---

