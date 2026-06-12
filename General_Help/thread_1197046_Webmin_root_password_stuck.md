---
title: "Webmin root password stuck"
date: 2009-06-25
forum: General Help
---

### Post by serodon on 2009-06-25
Alright. So I came into my company and was told to generally secure it and take over server admin duties.  Anyways I changed the webmin root password and now it's stuck in this odd loop.

I reach the login page and enter in root as user then the password.  Then it sends me to a page that says change temporary password, enter current and new password.  After I do that is sends me to a perl error page that says: 
**Error - Perl execution failed**

 Password changing is not enabled! at /webmin-1.480/password_change.cgi line 12.

I still have root access through SSH and I've already changed the password through ssh to no avail.

Any help would be greatly appreciated

---

