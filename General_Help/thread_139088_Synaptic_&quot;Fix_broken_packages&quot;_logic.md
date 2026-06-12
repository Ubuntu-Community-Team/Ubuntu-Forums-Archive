---
title: "Synaptic &quot;Fix broken packages&quot; logic"
date: 2006-03-03
forum: General Help
---

### Post by cronholio on 2006-03-03
Just a question: Sometimes "Fix broken packages" will remove the package in question, sometimes it will install the needed dependencies. What is the logic behind this? I guess a broken package is removed if the dependencies are not in the repos? Right?

---

### Post by jamyskis on 2006-03-03
AFAIK broken packages to be removed are done so usually because the installation of them was forced because certain dependencies couldn't be met - usually picky little things like an Ubuntu vs. Debian version of a library. If the dependency package is now in your sources, I guess it would install that instead, although I've never been that lucky.

---

### Post by cronholio on 2006-03-03
I just installed Opera, used the deb from the Opera site (it is not in the repos). Dependencies were unmet. Synaptic offered to fix it and I thought Opera would just be removed. Instead it installed the dependencies, which is very convenient.

---

### Post by Xian on 2006-03-03
[QUOTE=cronholio]Just a question: Sometimes "Fix broken packages" will remove the package in question, sometimes it will install the needed dependencies. What is the logic behind this? [/QUOTE]

If dpkg is used to install the program and there are unmet deps, that function will not then access non-local sources to try and resolve the problem. However, when you run the problem through APT it will first attempt to see if it can provide the needed libs through its available resources, which include online repositories. If this step is not successful then the only thing left is to remove the broken package.

---

