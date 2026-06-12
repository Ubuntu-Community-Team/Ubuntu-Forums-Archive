---
title: "pam_environment creates duplicate PATH entries"
date: 2010-08-22
forum: General Help
---

### Post by Ole_M on 2010-08-22
After installing TexLive the installer told me to add some entries to my PATH. As far as i know the recommended method is to use ~/.pam_environment.

The entry 
```
PATH DEFAULT=${PATH}:/usr/local/texlive/2009/bin/x86_64-linux
```works as it should, except that it adds the path -twice- to PATH:
```

echo $PATH
[...]/usr/local/texlive/2009/bin/x86_64-linux:/usr/local/texlive/2009/bin/x86_64-linux
```How can I prevent this?

Ole

---

### Post by Allar on 2011-10-26
Looks like i have the same problem. The ~/.pam_environment adds the entry to the PATH variable twice!
It would be nice if ~/pam_environment would't add duplicate entries.
```

PATH DEFAULT=.:${PATH}

``````

PATH=/usr/lib/lightdm/lightdm:.:.:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

---

