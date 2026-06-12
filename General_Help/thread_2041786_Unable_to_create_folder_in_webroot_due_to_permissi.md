---
title: "Unable to create folder in webroot due to permissions"
date: 2012-08-13
forum: General Help
---

### Post by chrissound on 2012-08-13
Hello everyone.  

I've setup a LAMP setup and I'm unable to create a new folder in my webroot

I basically have:
~/sites
~/sites/mysite

drwxr-xrwx 3 www-data chris 4096 2012-08-13 17:30 sites

I tried creating a new folder but I get this error: Error creating directory: Permission denied.  Can anybody clue me in on how I modify the permissions settings to allow me to create folders/drag other files in?

---

### Post by Vaphell on 2012-08-13
d[COLOR="DarkGreen"]rwx[/COLOR][COLOR="Blue"]r-x[/COLOR]rwx 3 [COLOR="DarkGreen"]www-data[/COLOR] [COLOR="Blue"]chris[/COLOR]

unless you log in as www-data you can't modify it (no w in group permissions). Strange thing is that 'others' (not-user, not-group) gets the full permissions. Did you mix it up? 775 would be more like it, not 757.

```
chmod 775 ~/sites
```

---

