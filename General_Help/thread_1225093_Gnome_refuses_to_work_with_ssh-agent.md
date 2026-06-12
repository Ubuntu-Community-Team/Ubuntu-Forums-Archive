---
title: "Gnome refuses to work with ssh-agent"
date: 2009-07-28
forum: General Help
---

### Post by alive1 on 2009-07-28
```
dak@dak:~$ ls -al .ssh/
total 60
drwx------  2 dak dak  4096 2009-07-28 10:27 .
drwx------ 44 dak dak 12288 2009-07-28 10:31 ..
-rw-------  1 dak dak  1101 2009-07-28 10:11 authorized_keys
-rw-------  1 dak dak  1264 2009-07-27 13:30 identity
-rw-------  1 dak dak  8720 2009-07-27 16:43 known_hosts

```Ubuntu simply refuses to ask me for a password to my identity file at startup.
It will, however ask me every time I connect to a new server.  The result is the same whether the file is called id_dsa, id_rsa or identity.

Also, if I add the identity file manually to ssh-agent, it will work with servers that have my pubkey - but still asks for my key password for servers which do not have my pubkey installed. Only if I leave the field empty and pres RETURN will it ask for my users password on the server.

If I run "ssh-add" in the Run Application dialog I get a password prompt with a nice blowfish icon in the top left.

My Ubuntu is a week-old 9.04 installation.

Please help. I'm going nuts trying to figure this out :(

---

### Post by alive1 on 2009-07-28
It works properly after I copied over my .pub key too. Apparently this is required.

---

### Post by dlafferty on 2010-03-16
BTW, which file did you mean when you said '.pub'?  A path would be useful.

---

