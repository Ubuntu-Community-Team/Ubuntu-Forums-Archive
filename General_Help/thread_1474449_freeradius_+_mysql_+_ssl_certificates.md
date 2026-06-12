---
title: "freeradius + mysql + ssl certificates"
date: 2010-05-06
forum: General Help
---

### Post by frankenstein1 on 2010-05-06
Hi,

Can i use freeradius + mysql + ssl certficates at the same time for autenticating users...or this does not make sense? I am a bit confused if i have to use one of them(mysql or ssl certificates) for autentication purposes.

I have read tutorials for using freeradius + mysql OR freeradius + ssl certificates. In  "freeradius + mysql" tutorial explains how to make the autentication using mysql... so the passwords and users are all stored inside a mysql db. In the other hand the  freeradius + ssl certificates   explains how to make the autentication using a file called "users" that stores all the users and paswords. 

So i am wondering if i can not make the radius server autenticate users using the credential fino from the mysql Db and using certificates too..or if each one are different methods to use.

Any ideas?

Cheers

---

### Post by Famicommie on 2010-05-06
They're independent methods, though it is possible to set passwords on ssl certificates. It should be possible to allow the user to use either a password or a certificate when they are authenticating but afaik both can't be required. Not conventionally, at least ;-)

From what I understand, using a passworded ssl certificate is by far the most secure option anyways. When you're generating the certificates make sure you have the bit strength set as high as the standard allows and apply passwords with decent entropy. Or you can skip the password; convenience is underrated.

---

