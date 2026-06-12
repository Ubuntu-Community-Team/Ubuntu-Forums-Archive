---
title: "samba server, with user access"
date: 2011-05-18
forum: General Help
---

### Post by Add1cken on 2011-05-18
hi again.

I'm having a really hard time finding this solution, so I hope someone can help me here.

I'm running "Ubuntu Server"
with "openssh-server"
and i want to run "samba server" along with my original "openssh-server"

I configured the samba config file (/etc/samba/smb.conf)
i want it to use, users as the authentication method.
and i if possible, i want samba to use the local users and their rights..
so i can just chmod the desired folders. (just like the openssh server uses.)


i added the user to samba user, even manually.

I add the desired folders, and it all works fine...

but when i found it through my windows machine
eighter i got right pass the user authentication, or i couldn't get pass it at all...

it's as if, it was looking for the username and PW in the wrong place.


can someone post an example of smb.conf file, where the samba server uses the local users, to allow access, and assign user rights.

---

### Post by Add1cken on 2011-05-19
bump !

anyone ?

---

