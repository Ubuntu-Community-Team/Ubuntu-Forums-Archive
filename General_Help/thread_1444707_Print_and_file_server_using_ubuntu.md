---
title: "Print and file server using ubuntu"
date: 2010-04-01
forum: General Help
---

### Post by Nemesis2 on 2010-04-01
Hi, 

I try to achieve something like sme server. 

I'd like to have the following: 
multiple user accounts with the following stuff
 - access to smb share (each user should have an own share)
 - access to printer (needs to report how many pages a user printed)

It would be perfect if I could add new users using a web interface. 

Are there any packages that may suit my needs? I tried google and the wiki pages but I found nothing that fulfills these requirements.

---

### Post by Chesamo on 2010-04-01
Did you look at Samba? Samba has a nice Web interface (for printers anyway).

---

### Post by Nemesis2 on 2010-04-01
How do I add new users using the web interface?

---

### Post by Chesamo on 2010-04-01
Add the users to Ubuntu. Samba will pick them up.

---

### Post by Nemesis2 on 2010-04-01
Thanks, I'll play around with samba and webmin. 

Why isn't webmin not in the standard repository? Are there any license isues?

---

