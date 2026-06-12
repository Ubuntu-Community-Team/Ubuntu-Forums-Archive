---
title: "Sharing WWW folder/ Not an owner problem"
date: 2010-08-23
forum: General Help
---

### Post by Partoni on 2010-08-23
I just got Apache and PHP all setup, but I want to share the apache WWW folder (/var/www). When I try to share the file, I get the following error:

> 'net usershare' returned error 255: net usershare add: cannot share path / var/www as we are restricted to only sharing directories we own. 
Ask the Administrator to add the line "usershare owner only = false" to the [global] section of the smb.conf to allow this.So, I tried to go into smb.conf and do what it told me too, but it is set to read only. And, I can't change it from read only because it is not owned by me, but it is owned by "root". 

I have placed myself in the admin group, but that didn't change anything. 

As you can tell, I am an Ubuntu newbie, so sorry if this question has an obvious answer. 

How do I either: make myself an owner of these files/folders, or share the WWW folder some other way. 

Thanks in advance for the help.

---

