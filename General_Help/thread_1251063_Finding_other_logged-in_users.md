---
title: "Finding other logged-in users"
date: 2009-08-27
forum: General Help
---

### Post by gu'an on 2009-08-27
I know for a fact that my friend (on XP) logged into my ubuntu linux through putty using a separate login user name, but when I tried to see the logged users list (using who, finger, last, lastb, lastlog), I dont see his login being registered - it just says he never logged in at all. It just shows my logins (even when I checked as a su).

Any suggestions/pointers?

Thanks.

**me and my friend worked together on transferring few files from mine to his'. So, I am not being paranoid here :D

---

### Post by gu'an on 2009-09-01
Really? Is it that obscure?

Its happening right now as I am typing this - he is remotely logged into mine (through putty on XP) and transferring files, but I am not able to see him with any of those commands above!

Can somebody please help?

---

### Post by BitJunkie on 2009-09-01
What kind of connection is it? ssh, ftp? If it's ftp, maybe try ftpwho.

---

### Post by gu'an on 2009-09-02
Sorry, I should have mentioned this earlier - its an SSH connection.

Just yesterday I got to know that I can use the following sequence to get what I needed:
```
/var/log/auth.log | grep "Accepted"
```But, I am still curious as to why the remote logins dont show up through who, finger, last, lastb and lastlog commands?!

---

