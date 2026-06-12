---
title: "Recursive chmod that follows symlinks"
date: 2012-08-22
forum: General Help
---

### Post by shkkmo on 2012-08-22
Is there anyway to modify file permissions in a way that traverses symlinks?

I see from reading docs from BSD and other operating systems that there is commonly a flag (-H or -L) that can be thrown on chmod to do this. However, not flag to do this appears to to available for the chmod command in ubuntu 12.04. Is there anyway to do this, is there a work around or another utility I can download? My google-fu is failing.

Here what I think would work in BSD for example:
chmod 755 -RLc /var/www/vhost/domain.tld/current/web

This should change the mode of the web folder, traverse it's tree and also follow symlinks in the web folder to change permissions in the linked plugin resources.


There must be some way to do this in Ubuntu, Right?

---

### Post by llamabr on 2012-08-22
You can get a little fancy:

[http://damonparker.org/blog/2007/06/27/recursive-chmod-tricks/](http://damonparker.org/blog/2007/06/27/recursive-chmod-tricks/)

---

