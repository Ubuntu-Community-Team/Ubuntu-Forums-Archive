---
title: "Installing Xerox drvers/ppd"
date: 2009-12-15
forum: General Help
---

### Post by gforster on 2009-12-15
We are demo-ing a Xerox 5655 mutlifunction copier/printer. There are linux drivers available from the Xerox site, but for redhat. They are in tar.gz format. When I untar the file, there is a setup file. I try to run it and get nothing. I try and change it  to a setup.sh and run it and get the error "cannot execute binary file." What the setup is supposed to do is extract a series of tar files called tar.z1, tar.z2 . . .tar.z9. When I try and do so manually, I get an error. What in the world am I supposed to do here?  i am sure it is possible, but I need a little help.

While i am at it - is there a multifunction copier that is recommended for us ubuntu users? We have used Ricoh in the past, and they've been ok with a little tweaking.

---

### Post by gforster on 2009-12-15
I found the answer I needed:

```
cat pkg_tar.z1 pkg_tar.z2 pkg_tar.z3 > pkg.tar.Z
```

and then I uncompressed the resulting file.

---

### Post by grantbow on 2010-02-04
Thank you.  It seems they want to obfuscate their software.  Not a good sign.

---

