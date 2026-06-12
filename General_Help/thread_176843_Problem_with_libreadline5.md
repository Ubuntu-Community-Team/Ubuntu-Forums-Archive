---
title: "Problem with libreadline5"
date: 2006-05-15
forum: General Help
---

### Post by elbaschid on 2006-05-15
Hey,

I have got a big problem with libreadline5 which I am not able to track down. Since the last system startup I have problems using gpg support in evolution and thunderbird (enigmail). Both exit with error message:

```
/usr/bin/gpg: symbol lookup error: /usr/local/lib/libreadline.so.5: undefined symbol: BC 
```

The same error message occurs whenever I try to install/update the package   "ubuntu-keyring". 

Can anyone help me with this? Where might this problem come from?

greetz,
baschdi

ps: gpg works just fine when I use it on commandline...

---

### Post by catslaugh on 2007-10-21
I had the same problem.  It's a collision between libreadline.so.5.2 (which is in /lib) and libreadline.so.5.0 (which is in /usr/local/lib).  A "dpkg-query -L libreadline5" shows that the libraries installed by that package are libhistory.so and libreadline.so, so remove /usr/local/lib/libhistory.so.5.0, /usr/local/lib/libhistory.so.5, /usr/local/lib/libreadline.so.5.0, and /usr/local/lib/libreadline.so.5.  Then tell Synaptic to reinstall ubuntu-keyring.

---

