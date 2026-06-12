---
title: "Wget a website : how to --exclude-files?"
date: 2010-01-21
forum: General Help
---

### Post by frenchn00b on 2010-01-21
Hello,

I am mirrored debs for my handheld linux, and I do wget with **-nc** because it has been interrupted. OK,
but I do not want all files and would like to exclude some "*GPE*.ipk" files.

I read the man, and it is obviously bit tricky for wget. Here is my ```
version:
~$ wget --version
GNU Wget 1.12 built on linux-gnu.

+digest +ipv6 +nls +ntlm +opie +md5/openssl +https -gnutls +openssl
-iri

Wgetrc:
    /etc/wgetrc (system)

```

Any wise ideas? 

thank you

---

### Post by slyyls on 2010-01-25
You can use the "--reject" option of wget.

It accepts wildcard parameters too.

[http://www.gnu.org/software/wget/manual/wget.html#Recursive-Accept_002fReject-Options](http://www.gnu.org/software/wget/manual/wget.html#Recursive-Accept_002fReject-Options)

---

