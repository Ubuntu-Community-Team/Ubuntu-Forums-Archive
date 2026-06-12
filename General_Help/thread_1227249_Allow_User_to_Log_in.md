---
title: "Allow User to Log in"
date: 2009-07-30
forum: General Help
---

### Post by zzzBrett on 2009-07-30
Is there a setting that specifies whether a user can log in to gnome?

I would like to log in as the user mythtv.  In webmin, there was a setting that said "not allowed to log in" or something of that sort... so I changed that and gave the user a regular password, but still don't have the option to log in.

How can I allow logging in with this user?

---

### Post by wojox on 2009-07-30
Never used webmin but apache yes. Try:

```
sudo /etc/init.d/apache2 restart
```

---

### Post by zzzBrett on 2009-07-30
> **wojox said:**
> Never used webmin but apache yes. Try:

```
sudo /etc/init.d/apache2 restart
```

hmm I dont think this has anything to do with apache.. I meant logging in to regular ubuntu via the log in window, not logging in to webmin / anything with the web server.

---

### Post by zzzBrett on 2009-07-30
bump

---

### Post by fyo on 2009-07-30
Perhaps adding the user manually through System->Administration->"Users and Groups" would solve your problem?

---

### Post by zzzBrett on 2009-07-30
> **fyo said:**
> Perhaps adding the user manually through System->Administration->"Users and Groups" would solve your problem?

I was thinking about that, but the user is already created.  If I delete the user, then recreate, will that mess up mythtv in any way?

---

