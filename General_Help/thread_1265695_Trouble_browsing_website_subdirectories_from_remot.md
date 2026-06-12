---
title: "Trouble browsing website subdirectories from remote PC"
date: 2009-09-13
forum: General Help
---

### Post by RP_Harris on 2009-09-13
I have installed website on ubuntu 8.04 hardy virtual server. LAMP has been installed, configured and verified working. The host server is VMWARE ESXi. I have set up subdirectory as follows
/var/www/word/ joomla is installed in /var/www/ and wordpress is installed into 
/var/www/word/ directory.
I can browse website and wordpress on localhost OK
[http://localhost/](http://localhost/) OK or [http://x.x.x.x/](http://x.x.x.x/) OK
[http://localhost/word/](http://localhost/word/) OK or [http://x.x.x.x/word](http://x.x.x.x/word) OK
[http://localhost/myphpadmin/](http://localhost/myphpadmin/) OK or [http://x.x.x.x/myphpadmin](http://x.x.x.x/myphpadmin) OK

However when I browse the site from a remote PC the following results are seen.
[http://x.x.x.x/](http://x.x.x.x/) OK
[http://x.x.x.x/word](http://x.x.x.x/word) Not OK CSS appears not to work just text and unable to login
[http://x.x.x.x/myphpadmin](http://x.x.x.x/myphpadmin) Not OK page cannot be displayed
Any thoughts or advice would be appreciated.
best regards

---

### Post by RP_Harris on 2009-09-15
Problem solved, it was simply a matter of binding the url of the wordpress site to the public interface, I found that it was bound to localhost, not good for remote access...
Issue resolved.

---

