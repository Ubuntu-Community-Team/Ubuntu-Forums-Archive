---
title: "Installing GPG key from browser"
date: 2009-09-03
forum: General Help
---

### Post by hwttdz on 2009-09-03
So my office has blocked whatever port it is that ubuntu uses to get gpg keys (11317?) which is a bit of a hitch.  So I ssh'd with x-forwarding to my home machine, and got the gpg key from the browser, anyways now I have it in a text file and I'm looking to install it.  Does anyone know how to install in this fashion?  Thanks.

Just found it, if you open up synaptic and settings->repository->authentication you can import the text file as a key.

---

### Post by geirha on 2009-09-03
Import it in Application -> Accessories -> Password and encryption keys, or with gpg in a terminal:
```
gpg --import *gpg-file*
```

---

