---
title: "How to add Ubuntu to Windows Domain"
date: 2011-11-08
forum: General Help
---

### Post by saichand on 2011-11-08
I am not able to join windows domain.
I tried in the following way.

---------------------------------------------------------------------------------
saichand@administrator:~$ sudo domainjoin-cli join xxxxxxxxxxxxxx.local saichand.t
[sudo] password for saichand: 
Joining to AD Domain:   xxxxxxxxxxxxxx.local
With Computer DNS Name: administrator.xxxxxxxxxxxxxx.local

[EMAIL="saichand.t@xxxxxxxxxxxxxx.LOCAL"]saichand.t@xxxxxxxxxxxxxx.LOCAL[/EMAIL]'s password: 

Error: Lsass Error [code 0x00000043]

Network name not found.. Failure to lookup a domain name ending in ".local" may
be the result of configuring the local system's hostname resolution (or
equivalent) to use Multi-cast DNS. Please refer to the Likewise manual at
http://www.likewise.com/resources/documentation_library/manuals/open/likewise-op
en-guide.html#ConfigNsswitch for more information.
saichand@administrator:~$ 
---------------------------------------------------------------------------------

I even tried with Likewise Active Directory Membership, it still shows the same error.

---

