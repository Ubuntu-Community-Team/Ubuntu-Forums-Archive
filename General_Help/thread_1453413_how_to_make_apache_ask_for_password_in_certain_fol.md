---
title: "how to make apache ask for password in certain folders"
date: 2010-04-13
forum: General Help
---

### Post by nerdy_kid on 2010-04-13
ok first off *please* dont say "go read the man page".  I need instructions for newbies :)

I basicly want certian folders to deny access to all clients exept those that supply the correct user name and password.  I tried following the directions [here]("http://eregie.premier-ministre.gouv.fr/manual/howto/auth.html") (for the basic authentication), but its not working.  Someone kind enough to help out a confused person like myself? :)

---

### Post by sandyd on 2010-04-13
use .htaccess and .htpassword to set the passwords

---

### Post by nerdy_kid on 2010-04-13
> **carlee said:**
> use .htaccess and .htpassword to set the passwords

i have ```

Deny from all
AuthType Basic
AuthName "Please enter username and password"
AuthUserFile /etc/apache2/passwords
Require user guest
Require valid-user

```
in .htaccess...sorry i really am a total newb at this, what would i put in .htpassword?

(i created the user "guest" with htpasswd -c /etc/apache2/passwords)

---

### Post by nerdy_kid on 2010-04-13
come on people!

---

### Post by nerdy_kid on 2010-04-13
ok mods i discovered the "server" forum so im reposting this there; sorry for the double threading :\

---

