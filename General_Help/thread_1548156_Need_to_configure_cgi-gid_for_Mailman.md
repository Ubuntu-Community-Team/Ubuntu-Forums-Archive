---
title: "Need to configure cgi-gid for Mailman"
date: 2010-08-07
forum: General Help
---

### Post by OnMyWay67 on 2010-08-07
New to Ubuntu, with intermediate Linux experience in an old Red Hat flavour. I'm trying to install and configure Mailman on a command line environment Lucid server. The web based Mailman admin module is failing to start because Apache is running as a non-default user, and Mailman is expecting the default www-data for it's cgi wrapper.
 
All the documented solutions I can find instruct me to run configure with the switch that adjusts the cgi-gid to the appropriate user. Unfortunately, I can 't find the configure command anywhere in any of the mailman directory structures etc. This instruction seems to precede instructions around doing a manual install, where as I used Aptitude. My experience with package installation on Ubuntu thus far has all been through Aptitude.
 
Does anyone know what needs to be done to get that cgi-gid fixed up?
 
Thanks in advance for your time. :)

---

### Post by OnMyWay67 on 2010-08-08
Anyone? :)

---

### Post by OnMyWay67 on 2010-08-10
Could someone recommend an alternate section to post this is so that I might get some ideas on my issue?

---

### Post by OnMyWay67 on 2010-08-22
Thanks guys! You've been awesome. ](*,)

---

