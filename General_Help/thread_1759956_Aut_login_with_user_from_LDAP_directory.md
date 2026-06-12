---
title: "Aut login with user from LDAP directory"
date: 2011-05-16
forum: General Help
---

### Post by natomb on 2011-05-16
Hello,

I want to setup automatic login on my Mythbuntu frontend machine (for this purpose, I think it is a "normal" Linux system).

I have setup an LDAP(S) directory on another machine and authentication against this LDAP from the frontend machine works fine. For the authentication I use nslcd.

Now, I want to enable automatic login on the frontend machine. However, when following the "traditional instructions", all I get is a blank screen (instead of a running XFCE session) on the frontend. Thus, I have to ssh into the frontend, change back the settings and everything works fine again.

I suspect that I missed something in the PAM settings. Is there anyone who can provide me with instructions on how to configure? Searching in google (eventually first 300 links) and various forums just yielded a "traditional auto login against local users".

Thank you very much
  Bjoern

---

### Post by natomb on 2011-08-28
With the new tutorial from the Ubuntu help pages it works very nice. Thank you to the author.

---

