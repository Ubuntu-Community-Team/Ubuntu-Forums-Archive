---
title: "Remove multiple packages"
date: 2011-02-15
forum: General Help
---

### Post by megabuffen on 2011-02-15
Is there any way to quickly remove multiple related packages from the command line instead of having to enter the name of every single one? I am trying to remove OpenOffice from my server running 10.04. It would work nicely if I could get a list of packages without line breaks, such as the list displayed by aptitude when upgrading. That way I could just paste the package list into the terminal. However, "aptitude search 'openoffice'" dumps a long list on many lines that cannot be used that way.

Any ideas?

---

### Post by lisati on 2011-02-15
If you run it without command line options, aptitude displays a text-based ui which you might be helpful.

---

### Post by TeoBigusGeekus on 2011-02-15
```
sudo apt-get remove openoffice*.*
```
should do it.

---

### Post by megabuffen on 2011-02-15
Thanks! That did it. Regular expressions are awesome!

---

