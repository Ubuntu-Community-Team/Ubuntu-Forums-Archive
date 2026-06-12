---
title: "Webmail &amp; Firefox encryption algorithms"
date: 2006-05-02
forum: General Help
---

### Post by JoeS on 2006-05-02
I got this message when I tried to connect to my webmail with Firefox:

"Firefox and webmail.shaw.ca cannot communicate securely because they have no common encryption algorithms."

Can anyone help.  I'm not familiar with encryption algorithms.

---

### Post by cgjones on 2006-05-02
It looks like they are using RC4 (40 Bit), which is definitely pretty weak by today's standards. Did Firefox give you an option to continue?

---

### Post by dcstar on 2006-05-03
[QUOTE=cgjones]It looks like they are using RC4 (40 Bit), which is definitely pretty weak by today's standards. Did Firefox give you an option to continue?[/QUOTE]
Old issue, you have to go into about:config and set to true:
```
security.enable_ssl2
security.ssl2.rc4_40
security.ssl3.rsa_rc4_40_md5
```

---

