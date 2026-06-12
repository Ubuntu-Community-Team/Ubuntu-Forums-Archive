---
title: "Shared Folders"
date: 2006-01-20
forum: General Help
---

### Post by compuguru on 2006-01-20
I am trying to setup a shared folder (/var/www) so that my Windows XP PC and get to it.  I've gone through some tutorials on how to do it, but they are not working.  The folder is not showing up.  And when I try to access my Ubuntu computer by clicking on the Icon in my Network Computers, it prompts me for a login.
Could someone please give me specific on how to accomplish this?

---

### Post by ptmurphy on 2006-01-20
I presume you are using Samba?

If so, you must (if security is setup) setup a user and password to login to the shared folders.

Use smbpasswd to add a samba password to the Linux user.  Then when it asks for a password, enter that username and password (the samba password, not the Linux password.

sudo smbpasswd -a <username>

As a side note, if you have the same username and password on teh XP box that username and password will be used, so it will not prompt you each time.

Hope that helps.

---

### Post by audax321 on 2006-01-20
If you don't care for the authentication, here are directions to setup the share:

readable and writeable with no authentication:
[http://www.ubuntuguide.org/#sharepublicfoldersreadwritesecurityshare](http://www.ubuntuguide.org/#sharepublicfoldersreadwritesecurityshare)

reading (not writeable) with no authentication:
[http://www.ubuntuguide.org/#sharepublicfoldersreadwritesecurityshare](http://www.ubuntuguide.org/#sharepublicfoldersreadwritesecurityshare)

---

### Post by compuguru on 2006-01-20
[QUOTE=audax321]If you don't care for the authentication, here are directions to setup the share:

readable and writeable with no authentication:
[http://www.ubuntuguide.org/#sharepublicfoldersreadwritesecurityshare](http://www.ubuntuguide.org/#sharepublicfoldersreadwritesecurityshare)

reading (not writeable) with no authentication:
[http://www.ubuntuguide.org/#sharepublicfoldersreadwritesecurityshare](http://www.ubuntuguide.org/#sharepublicfoldersreadwritesecurityshare)[/QUOTE]
Great!  The first one was what I as looking for.  Thanks! :)

---

