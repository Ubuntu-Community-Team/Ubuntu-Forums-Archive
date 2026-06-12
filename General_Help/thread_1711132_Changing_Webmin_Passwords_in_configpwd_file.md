---
title: "Changing Webmin Passwords in config/pwd file"
date: 2011-03-20
forum: General Help
---

### Post by OldManRiver on 2011-03-20
All,

I installed WebMin on my machines to resolve some problems I had with backups.  Got things working and then clicked on the option to bring all the Linux users into WebMin.  Now I'm locked out of the program, because WebMin does not recognize any of the users as administrators, will not let "root" login, and so I have no access to any of the functions any longer.

I'm sure there is a config file controlling this.  Where is it and what do I change to get back to my old settings, or add admin rights to the linux user(s).

Thanks!

OMR

---

### Post by OldManRiver on 2011-03-20
All,

Nevermind!

I found that the file:

/etc/webmin/webmin.acl

contains the keys of what each user has access to in WebMin, so copied the set for root to the other users and now working fine.

One more question.

My SAMBA server is showing up under the "Un-used" portion and since it is active need to move it to the "Servers" section.

How is that done?

Thanks!

OMR

---

### Post by OldManRiver on 2011-03-29
All,

Oh hey forgot to upgrade this.  Found the "Reload" option at the bottom.  Got this working on 4 machines now.  One machine is erroring on bacula director so went to their support page and sent problem to the email list.

Another machine is blowing up on mysql, and I posted on that elsewhere on this forum.

Thanks!

OMR

---

### Post by OldManRiver on 2011-05-02
All,

Never got a response from the Bacula support team, so on my own again!

OMR

---

### Post by OldManRiver on 2011-05-13
All,

Still nothing from the baccula folk, but that is seperate issue, so closing this one.

Thanks!

OMR

---

