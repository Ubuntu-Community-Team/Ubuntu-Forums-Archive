---
title: "problems with encfs (version, boost library)"
date: 2010-10-02
forum: General Help
---

### Post by ductipus on 2010-10-02
I've used encfs on another linux system to create an encrypted file structure. The other system is gentoo with encfs 1.72. I've tried to mount the encrypted file structure in xubuntu which has encfs 1.5 and get an "Archive exception: class version". There's no newer version in Synaptic and I'm guessing that the error is an incompatibility issue with the structure made by the newer version of encfs. Is there a way to install a newer version of encfs through the ubuntu packaging system, or other way around this?

I've also tried to compile encfs 1.72 manually but I get a configure error "We could not detect the boost libraries ...". I suppose there is a way to tell configure to use the same boost libraries that ubuntu's packaged version does, but how?

---

