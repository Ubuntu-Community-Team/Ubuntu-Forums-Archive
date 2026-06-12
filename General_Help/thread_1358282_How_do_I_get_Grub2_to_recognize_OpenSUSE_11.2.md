---
title: "How do I get Grub2 to recognize OpenSUSE 11.2?"
date: 2009-12-18
forum: General Help
---

### Post by tuahaa on 2009-12-18
I've installed Ubuntu 9.10 as a dual boot, side by side with OpenSUSE 11.2. After installation however, Grub 2 doesn't list OpenSUSE 11.2 in the options for booting! How do I edit grub to list OpenSUSE?

---

### Post by tuahaa on 2009-12-18
Bump (I didn't want this to get buried, sorry)

---

### Post by tuahaa on 2009-12-18
I found this at the wiki and it fixed my problems. :)> Following this thread on the forums, users have seemed to come up with a Karmic work around for fixing your dual-boot problems...```

$ sudo apt-get install --reinstall libdebian-installer4
$ sudo os-prober
$ sudo update-grub
```

---

