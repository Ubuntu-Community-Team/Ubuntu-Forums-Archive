---
title: "Kerberos autentication, pam problems..."
date: 2011-07-29
forum: General Help
---

### Post by JoZ on 2011-07-29
Hi... successfully configured kerberos... but I still can't login to my ubuntu box... 

Here is what I get in the log...

```
pam_krb5(gdm:auth): user xy authenticated as xy@mydomain.com
gkr-pam: error looking up user information
pam_unix(gdm:account): could not identify user (from getpwnam(rosa))
```

Does anyone know what did I forget????

thank you very much!!!

JoZ

---

### Post by JoZ on 2011-08-11
Bump???

---

### Post by JoZ on 2011-08-17
It ended up looking left and right and calling a couple of Ubuntu guru's... 
Tried different things that you can find on Internet:
I set ntpdate in order to keep sync with my Domain Controller
reconfigured Pam with several different parameters

When they told me it was time to change scripts at rc.levels I ended up installing the last version of Likewise...

The version from the website works great, the one from the repositeries seams to suffer of the same problem...

Pity of this... would had like not to install 3rd party elements for such things.

---

