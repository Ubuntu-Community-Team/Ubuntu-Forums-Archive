---
title: "userrights for webdesign in /var/www"
date: 2006-03-19
forum: General Help
---

### Post by quate on 2006-03-19
Hi,

I'm trying to wright files to my /var/www/quate thing (sorry, I'm not english and do not know all the approriate words), but I cannot access this. Before I could access /var/www and I copied some files to test if php scripts were loaded correctly. But the scripts did not load, so I did the following, which solved this loading problem:

sudo a2enmod php5
sudo (apache) restart

However, since then, the scripts are being load correctly, but I have no longer writing access. What happened? I am member of www-data, and gave everthing in /var and /var/www 755. Do I need to change this?

tnx

---

### Post by quate on 2006-03-19
!!!!! off course !!!!! I'm member of www-data, but this doesn't make me owner. So the group needs writing to. I changed the rights in 775. I can now work ok, but is this safe (775)?

---

