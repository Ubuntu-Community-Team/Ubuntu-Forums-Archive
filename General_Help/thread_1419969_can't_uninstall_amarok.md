---
title: "can't uninstall amarok"
date: 2010-03-02
forum: General Help
---

### Post by brandon89 on 2010-03-02
hey im trying to uninstall amarok (i keep running into problems setting it up), but now whenever i try, i get this error

```

dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing amarok (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 amarok
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:

```

it doesnt actually recover anything though.  btw, im running 9.10 ubuntu.  thanks for any help

---

### Post by zvacet on 2010-03-02
```
sudo dpkg --remove --force-remove-reinstreq package_name
```

---

### Post by brandon89 on 2010-03-02
EDIT: that didnt work but i did some more searching and i think i figured it out.  at least i can now install other packages.  thanks for the help though

---

