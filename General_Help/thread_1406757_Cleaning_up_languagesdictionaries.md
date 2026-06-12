---
title: "Cleaning up languages/dictionaries"
date: 2010-02-14
forum: General Help
---

### Post by Admiral_Payne on 2010-02-14
Is it possible to get rid of all the extra language dialects like en_ZA, en_AU, en_US?
Now when I use the Firefox and/or Thunderbird language check thing, I want to be able to swap between nl_NL and en_GB without looking through the whole list of options.

Hiding all the other options might also be a good fix, as long as the language list isn't so darn huge.
Right now all languages are also being displayed double, eg: "en_US" and "English / United States", "en_GB" and "English / United Kingdom".

Thanks,

---

### Post by webdevelopment on 2010-02-16
same question, where do i get EN US?

---

### Post by Admiral_Payne on 2010-02-16
> **webdevelopment said:**
> same question, where do i get EN US?
That's usually your standard language pack :P I presume you mean to get rid of all the other ones instead?

---

### Post by Admiral_Payne on 2010-02-26
Bump.. Anyone knows?

---

### Post by bumanie on 2010-02-26
Look [here]("http://ubuntuforums.org/showthread.php?t=1387200&page=1") and then follow the link on the page in post number 3.

---

### Post by Admiral_Payne on 2010-02-26
:( I've installed it but now I've got the ones I wanted to keep double, and all the entries are still there.

How can I reconfigure that program to try to toggle a few other settings?
```

$ sudo dpkg --configure localepurge
dpkg: error processing localepurge (--configure):
 package localepurge is already installed and configured
Errors were encountered while processing:
 localepurge

```

Edit: Found settings in /etc/locale.nopurge

---

