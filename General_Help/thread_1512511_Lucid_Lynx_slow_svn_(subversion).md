---
title: "Lucid Lynx slow svn (subversion)"
date: 2010-06-18
forum: General Help
---

### Post by fbaralli on 2010-06-18
Hi,

I recently made a fresh install of 10.4 64bit, and I experienced extremely slow svn+http (not https) connections to my usual repositories since then.

Does this sound familiar to you?

Thanks a lot
F.

---

### Post by leorolla on 2010-06-18
Here everything is fine. What did Google say?

---

### Post by fbaralli on 2010-06-18
> **leorolla said:**
> Here everything is fine. What did Google say?

Google says a lot about troubles with ssl certificates but not much on plain http, unfortunately.

---

### Post by telefunken on 2010-07-02
Did you solve this? I have the same problem with both http and https. The same repos worked fine in 9.10, and they are super slow now...

---

### Post by fbaralli on 2010-07-05
Hi,

I haven't been working on it for two weeks (I was out of office).
Today I tried again and svn asked
```
Password for '(null)' GNOME keyring: 
```

I typed my password (we are in an LDAP environment) and it worked a lot faster!!!

I know that the administrator have updated both the server and my machine during my absence but nothing has been changed on the configuration of svn on both sides.

Cheers
Francesco


> **telefunken said:**
> Did you solve this? I have the same problem with both http and https. The same repos worked fine in 9.10, and they are super slow now...

---

### Post by telefunken on 2010-07-05
Yes, same story for me! Seems like something was updated recently, nice...

//Adde

---

