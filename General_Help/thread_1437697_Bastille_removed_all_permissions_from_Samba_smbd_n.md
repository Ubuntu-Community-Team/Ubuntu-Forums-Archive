---
title: "Bastille removed all permissions from Samba smbd nmbd files"
date: 2010-03-24
forum: General Help
---

### Post by billzeeabob on 2010-03-24
After running Bastille to harden my server, Samba stopped working. It had asked me if I would like to disable Samba during the configuration and I selected 'no' so it should not have done this.

When I tried:

```
sudo /etc/init.d/samba restart
```

Nothing happened. I found in the script, if it does not detect smbd and nmbd running, it just exits -- no error message, just simply does nothing.

I found that /usr/sbin/smbd and /usr/sbin/nmbd both had all permissions removed. I set them back to 755 and restarted samba normally. All is good now.

If anyone can direct me to where/who to advise of this issue, it would be greatly appreciated.

---

### Post by billzeeabob on 2010-03-26
Okay, not funny. The permissions were removed again. Any ideas on what is removing them?

---

