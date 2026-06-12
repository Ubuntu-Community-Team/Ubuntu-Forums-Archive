---
title: "Okular can not open any pdf files"
date: 2011-05-31
forum: General Help
---

### Post by Robbyx on 2011-05-31
Since upgrading to 11.04 I am finding that Okular gives an error message on every file that I try open with it. I have just installed the latest update and it still reports that it is unable to open the file. Even a file on the desktop gave the same error.

Has anyone else had the same problem. What did you do to solve it?

---

### Post by tredegar on 2011-05-31
"Upgrading" ubuntu is still full of bugs.

The general advice is to backup your personal files, make a fresh install, then restore your personal files.

I don't know why Canonical still offer this "upgrade" option, because it has been broken for years.

That said, maybe if you told us the exact error ocular gives you, and which version of ubuntu you upgraded *from*, maybe someone can help you better.

---

### Post by Robbyx on 2011-05-31
There are two error messages:

Can not find a plugin which is able to handle the document that is being passed.

Can not open the pdf (and gives the full path.)

---

### Post by tredegar on 2011-06-03
You have only answered one of my questions.

---

### Post by Robbyx on 2011-06-03
Ubuntu 10.10 to 11.04

---

### Post by linuxinstalledfromhdd on 2011-06-03
I would simply try to reinstall each of those programs from the software control center, including the adobe reader acroread as well.  Make sure you have the ind and partner repos available in synaptic.

---

### Post by tredegar on 2011-06-04
Agreed. If reinstalling Okular doesn't fix the problem, I'd recommend backing up your personal data, and starting with a fresh install of 11.04

---

### Post by SeijiSensei on 2011-06-04
I've often found that removing the configuation files for an application from ~/.kde/share can resolve problems like these.  For okular, you need to delete a directory, ~/.kde/share/apps/okular and two files, ~/.kde/share/config/okularrc and ~/.kde/share/okularpartrc.

See if that helps.

I keep /home on a separate partition and have found things work better when upgrading if you move .kde to .kde.old first and let the new version create its own configuration.  I keep the old version so I can copy selected items from it to the new configuration for specific applications.

---

### Post by Chronon on 2011-06-04
> **SeijiSensei said:**
> 
I keep /home on a separate partition and have found things work better when upgrading if you move .kde to .kde.old first and let the new version create its own configuration.  I keep the old version so I can copy selected items from it to the new configuration for specific applications.
This sounds like fantastic advice and is relevant for fresh installs too if you have a separate /home partition.  I too have noticed that most upgrade problems come from incompatible settings retained from old versions.

---

### Post by Robbyx on 2011-06-04
I have ocular working by:

Removing all KDE files via synaptic.
Deleting .kde
reistalling okular and allowing the dependencies to install as well.

Thank you everyone who tried to help me. Very much appreciated especially as it is now working properly

---

### Post by Talion86 on 2011-06-16
Deleting .kde and reinstalling all kde packages did not help me to get PDFs working in okular on Xubuntu 10.04.2 LTS (Lucid)

I got it working by following this hint:
[http://okular.kde.org/faq.php#okularnoplugins](http://okular.kde.org/faq.php#okularnoplugins)
```
kbuildsycoca4 --noincremental
```

---

