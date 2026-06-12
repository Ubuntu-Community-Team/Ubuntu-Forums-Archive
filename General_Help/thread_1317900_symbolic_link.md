---
title: "symbolic link"
date: 2009-11-07
forum: General Help
---

### Post by iMisspell on 2009-11-07
I have Ubutnu 8.04 server running with Apache and have created a symbolic-link inside /var/www/ pointing to /usr/lib/cgi-bin/ everything works fine.

Now...
On my desktop (Ubuntu 9.04) i have the servers /var/www/ mounted via fstab to /bla/ (everything is working fine). On my desktop i also have apache running so the desktop also has /usr/lib/cgi-bin/.
When ever i click into the servers mounted folder and try to access the /cgi-bin/ folder, i am sent to my local-desktops /usr/lib/cgi-bin/ folder and not the servers /usr/lib/cgi-bin/.

On the server i created the symbolic link like so...
```
ln -s /usr/lib/cgi-bin/ /var/www/
```
tring different link options only gets me "*hard link not allowed for directory*"

Is there a way around this ?

_

---

### Post by geirha on 2009-11-07
Been a long while since I messed around with apache, but there's probably a configuration option that decides how symlinks should be handled.

When you access the cgi-bin folder, does the url change from http:// to file:// ?

---

### Post by iMisspell on 2009-11-07
hey there.. thanks for the replay...
> **geirha said:**
> When you access the cgi-bin folder, does the url change from http:// to file:// ?

Sorry i should have been a little more clear.
The problem i am having is all through the desktop interface, the file manager (have yet to config the desktops apache (just installed), so im not concernet with that yet)...

Just came up with alittle work around (not sure if its flawed, only testing right now).
Deleted the cgi link off the server, created a cgi-bin samba share to /usr/lib/cgi-bin/ on the server, mounted that cgi share to the desktop inside the already mounted www mount.
Seams to be working, still have more testing to do.

---

