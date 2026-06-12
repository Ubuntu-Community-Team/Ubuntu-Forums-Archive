---
title: "Port Command In Ubuntu"
date: 2009-08-24
forum: General Help
---

### Post by carloc on 2009-08-24
Hi,

i've seen several posts regarding using the port command.

What package do I install in ubuntu to use it?

> sudo port install py25-hashlib
I want to install py25-hashlib because i'm getting no module named _md5 errors.

i can't seem to find it anywhere.

how do i resolve this error?
also, how do i install openssl-utils package?

Thanks
:confused:

---

### Post by dearingj on 2009-08-24
2 things:
1) As far as I can tell, there is no 'port' command in Ubuntu. What it looks like you want is 'apt-get'.
2) I couldn't find anything called py25-hashlib, but I did find 'python-crypto' and 'python-ncrypt'. Python-ncrypt is probably the one you want, as its description says it provides the md5 algorithm.

It can't hurt to install both packages, so open a terminal and type (or copy & paste):
```
sudo apt-get install python-crypto python-ncrypt
```

Hope this helps.

---

### Post by P4man on 2009-08-24
Maybe its easier you tell us what you're trying to achieve. None of the packages you mentioned seem to exist for ubuntu (or even linux). When i google on it, i seem to be getting OS-X results mostly. Are you trying to follow an OS-X howto on ubuntu or something?

---

### Post by dearingj on 2009-08-24
Also, there is no 'openssl-utils' package in Ubuntu, at least that I could find. There is, however, a package called 'openssl' which "contains the openssl binary and related tools." Install it using the command
```
sudo apt-get install openssl
```

I'd also recommend installing openssl-blacklist, which contains a list of known bad encryption keys.

---

