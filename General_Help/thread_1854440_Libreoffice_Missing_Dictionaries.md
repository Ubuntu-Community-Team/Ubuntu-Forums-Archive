---
title: "Libreoffice Missing Dictionaries"
date: 2011-10-04
forum: General Help
---

### Post by EBrune3 on 2011-10-04
Libreoffice stopped spell checking, so I checked the location for the dictionary files.  /home/.libreoffice/3/user/wordbook/standard.dic is missing.  Any idea how to repair this?
My selected language is en_us.  I have tried uninstalling/re-installing hunspell.
Thank you for any suggestions you might have.

---

### Post by Toz on 2011-10-08
My problem was that my locale is en_CA but the language dictionaries installed were en_GB and en_US. I renamed the en_GB files to en_CA and got my spell check to work.

What is your locale? You can find out by opening a terminal window and typing in the following command:
```
locale | grep LANGUAGE
```

Then, what language dictionaries are installed:
```
ls /usr/share/hunspell
```

Post back your results.

---

