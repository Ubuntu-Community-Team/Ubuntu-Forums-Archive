---
title: "k3b: &quot;cdrdao will be run without root privileges&quot;"
date: 2006-02-03
forum: General Help
---

### Post by harty83 on 2006-02-03
Every time I open k3b, I get the message "cdrdao will be run without root privileges"  It tells me to fix by opening K3bSetup2.  But when I open K3bSetup2, there is nothing there but the buttons "Help," "Defaults," "OK," "Apply" (greyed out), and "Cancel."  There is a box where something is suppose to be, but there is nothing but a big fat void.  

How can I a) fix the setup issue or b) manually set cdrdao to have root priviliges?

Thanks!
Alan

---

### Post by edeuxk on 2006-02-03
im having the same problem using dapper drake
in console i get this output:

k3bsetup
QMultiInputContext::changeInputMethod(): index=0, slave=xim
iSession management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
QMultiInputContext::changeInputMethod(): index=0, slave=xim

[edit]

i fixed it bij making cdrdao run suid

# sudo chmod +s /usr/bin/cdrdao

---

### Post by bored2k on 2006-02-03
Have you guys tried running K3bsetup2 with the kdesu command? 

edit: edeuxk fixed it.

---

