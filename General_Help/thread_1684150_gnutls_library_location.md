---
title: "gnutls library location"
date: 2011-02-08
forum: General Help
---

### Post by Rodayo on 2011-02-08
So I'm trying to build wireshark from source and I'm running into a persistant little error on ./configure and make

When I run the configure, I get an error message about a syntax error in one of the if blocks in the configure bash script. The if block was checking for gnutls to be installed(which it is)

I looked over the code, it wasn't terribly crucial to the build so I just took the end result(which was setting a variable) moved it outside the if block and commented out the block.

After that the configure ran without any problems. Although I got this as one of the messages:
> Use gnutls library : no

So afterwards I ran the make and it fails with this error message:
> @LIBGNUTLS_LIBS@: No such file or directory

So it's pretty clear that the build is not able to locate the gnutls library. Digging around on my system I found the library at /usr/include/gnutls. So I set that as the value of LIBGNUTLS_LIBS with an export command but that did not work either.

Anyways, if you don't know how to assist me on those steps, perhaps you can tell me where the gnutls library is located. I even checked the INSTALL file for it and it said thats the location they are installed to by default.

Any sort of help would be appreciated. =]

---

