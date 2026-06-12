---
title: "Problem with Centrify and local accounts"
date: 2012-01-20
forum: General Help
---

### Post by JAZ1976 on 2012-01-20
I have Centrify Express installed and set up on my Ubuntu 11.10 server, and it is allowing Active Directory accounts to log in, but I just added a local user account with no password and it is not letting me log in with that account. What do I need to do to get this account to log onto the server?

---

### Post by sumana.annam on 2012-01-20
Centrify software does not interfere with local logins at all. As  soon as Centrify daemon detects the user is not an Active Directory  user, the authentication is passed over to the local PAM modules. 
 
 May be Centrify software is detecting it as an AD Account. Are you sure  there is no AD account with the same username as local one ? 
 
You  can try adding this local user account into  /etc/centrifydc/user.ignore, restart Centrify express daemon and run  adflush. Try login again. 
 
 Also instead of blank password, set a password and check if login works ?
 
 Thanks

---

### Post by sumana.annam on 2012-01-20
The issue got resolved after setting password for the local account. For more details refer to the same post under [Centrify Express Community.]("http://community.centrify.com/t5/DirectControl-Express-for-UNIX/Problem-logging-on-with-a-local-Linux-user-account/m-p/3436#M1089")

---

