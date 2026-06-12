---
title: "locales/post-installation script -- HELP!!!!"
date: 2006-06-07
forum: General Help
---

### Post by BlakCheez on 2006-06-07
Every time I try to do anything involving installing/removing packages or whatever, it always puts out this:

> Setting up locales (2.3.5-1ubuntu12.5.10.1) ...
Generating locales...
  Usage:./usr/sbin/validlocale <locale>...Try `localedef --help' or `localedef --usage' for more information.
dpkg: error processing locales (--configure):
 subprocess post-installation script returned error exit status 4
Errors were encountered while processing:
 locales

and doesn't finish whatever it is.  It's getting on my nerves, because it won't let me upgrade to Dapper Drake.  please please please, i need help!!!

---

### Post by ifokkema on 2006-06-07
[QUOTE=BlakCheez]It's getting on my nerves, because it won't let me upgrade to Dapper Drake.  please please please, i need help!!![/QUOTE]

What happens if you type
```
sudo dpkg-reconfigure locales
```

You should get a list of possible locales. Get at least a few selected, but not too many at first (first see if we can get it to work). Then select OK. It should go about and install your selected locales.

---

