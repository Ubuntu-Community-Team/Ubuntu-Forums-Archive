---
title: "dpkg --configure -a"
date: 2009-07-04
forum: General Help
---

### Post by dav1d14 on 2009-07-04
I'm new to ubuntu so please go easy and try to explain this aswell as possible. thanks.

Whenever I try and update current programs, or or run my package manager I get this error notice, 


E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

please help me fix this, thanks

---

### Post by overdrank on 2009-07-04
> **dav1d14 said:**
> I'm new to ubuntu so please go easy and try to explain this aswell as possible. thanks.

Whenever I try and update current programs, or or run my package manager I get this error notice, 


E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

please help me fix this, thanks

Hi and welcome, if you open the terminal located under applications, accessories, and enter the command given ```
sudo dpkg --configure -a
```this should correct the issue.

---

### Post by Brandel Valico on 2009-07-04
open a terminal "Applications -> Accessories -> Terminal

Then run the suggested command

"sudo dpkg --configure -a'"

It will ask for your password

type it and hit enter (You won't see it but it is being typed)

---

### Post by dav1d14 on 2009-07-04
-desktop:~$ sudo dpkg --configure -a
[sudo] password for ferguson: 
Setting up java-common (0.30ubuntu4) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...

this is what i got? Does that mean it is complete?

---

### Post by overdrank on 2009-07-04
> **dav1d14 said:**
> -desktop:~$ sudo dpkg --configure -a
[sudo] password for ferguson: 
Setting up java-common (0.30ubuntu4) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...

this is what i got? Does that mean it is complete?

Now try and update
```
sudo apt-get update && sudo apt-get upgrade
``` and see if you receive any errors.

---

### Post by michy99 on 2009-07-04
Looks good. Does your package manager work ok now?

---

### Post by dav1d14 on 2009-07-06
Thanks you guys. everything seems to be working fine.

---

