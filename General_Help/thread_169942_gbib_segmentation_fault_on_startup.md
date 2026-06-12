---
title: "gbib segmentation fault on startup"
date: 2006-05-03
forum: General Help
---

### Post by unperson on 2006-05-03
I'm trying out the bibtex bibliography mangement software gBib.  I installed it (from the repository) and used it fine on my work computer running Hoary, but when I installed gBib (again from the appropriate repository) on my home system running Breezy, it segfaults immediately when I try to start it from the command line.  I can't even get it to output the version with the --version flag.  Has anyone else had this problem or does anyone know what might be going on here?

---

### Post by unperson on 2006-05-03
**Update**: I removed the gbib package on my breezy machine using apt-get, and then I did

```
sudo apt-get build-dep gbib; sudo apt-get --compile source gbib
```

to install the source package and dependancies from the source repository and then compile a deb from source.  I installed the deb this produced and that seems to work.

I still don't know what's wrong with the binary version and if it's just specific to my machine.  I don't see anything in the ubuntu bug tracker about it.  I can use the version I compiled from source, but I'm wondering if I should file a bug report about the binary version.  If anyone else can tell me if they have the same problem that would be a big help.

---

