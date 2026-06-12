---
title: "getting filezilla to use the SSH2 key stored in Seahorse"
date: 2009-12-15
forum: General Help
---

### Post by Polygon on 2009-12-15
Hello,


I can't seem to get FileZilla to use the SSH2 key that i have stored in the gnome keyring manager (seahorse).

My key is imported into seahorse fine....

[[IMG]http://img94.imageshack.us/img94/3618/screenshot006a.th.png[/IMG]](http://img94.imageshack.us/i/screenshot006a.png/)

and if i ssh into my hosting, it works fine as well and does not ask for my password:

[[IMG]http://img130.imageshack.us/img130/6637/screenshot002uq.th.png[/IMG]](http://img130.imageshack.us/i/screenshot002uq.png/)

And filezilla claims that it checks the SSH_AUTH_SOCK environment variable if it is set, but it IS set and it still doesn't work:

[[IMG]http://img69.imageshack.us/img69/4294/screenshot003f.th.png[/IMG]](http://img69.imageshack.us/i/screenshot003f.png/)


My filezilla settings:

[[IMG]http://img94.imageshack.us/img94/945/screenshot005i.th.png[/IMG]](http://img94.imageshack.us/i/screenshot005i.png/)


anyone have any ideas? =/

---

### Post by Polygon on 2009-12-17
UPDATE: I'm not sure what happened, or maybe ubuntu just needed to restart, but now filezilla uses the key from Seahorse and it all works fine now.

Simply select SFTP in the servertype

Select "Normal" for the logon type

make sure the password field is empty, and just hit connect, and it connected, seahorse asked for my SSH private key passphrase and I connected. yay =)

---

### Post by graysky on 2010-09-27
Man, same problem I have... I followed your steps but filezilla doesn't connect.  Any thoughts?

```
Error:	ssh_init: Name or service not known
Error:	Could not connect to server
```

EDIT: logging out solved this issue.  I suspect it has to do with multiple key regenerations on my part.

---

