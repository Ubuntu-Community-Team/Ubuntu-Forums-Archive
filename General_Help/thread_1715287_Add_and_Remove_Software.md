---
title: "Add and Remove Software"
date: 2011-03-26
forum: General Help
---

### Post by AnotherMuggle on 2011-03-26
I have noticed that lots of the packages in Kubuntu Software Management -> Add and Remove Software are duplicated with a different description: "4:4.4.2-0ubuntu1" and "4:4.4.5-0ubuntu1".

Can anyone tell me what these numbers represent so I can decide which of the two packages to install?  If you need an example then please search of KBreakout.

Thanks in advance.

---

### Post by ankspo71 on 2011-03-26
Hi,
Please see this link explaining Ubuntu's package version information.
[http://www.ducea.com/2006/06/17/ubuntu-package-version-naming-explanation/](http://www.ducea.com/2006/06/17/ubuntu-package-version-naming-explanation/)
Additionally, the "4.4.2" and "4.4.5" normally represent the versions of packages on their own homepages too. 

Ubuntu normally doesn't keep many packages with multiple versions on their repositories, but in some cases they do. Multiple versions can also be the result of using different repositories, for example, if you used an additional repository to upgrade KDE from 4.4.2 to 4.4.5, you might find many KDE packages with multiple versions. 

If you are using KDE 4.4.5, then it would be better to install 4.4.5 version of Kbreakout. (Most KDE applications carry the same version as the version of desktop they were meant for.)

Hope this helps.

---

### Post by AnotherMuggle on 2011-03-27
> **ankspo71 said:**
> Hi,
Please see this link explaining Ubuntu's package version information.
[http://www.ducea.com/2006/06/17/ubuntu-package-version-naming-explanation/](http://www.ducea.com/2006/06/17/ubuntu-package-version-naming-explanation/)
Additionally, the "4.4.2" and "4.4.5" normally represent the versions of packages on their own homepages too. 

Ubuntu normally doesn't keep many packages with multiple versions on their repositories, but in some cases they do. Multiple versions can also be the result of using different repositories, for example, if you used an additional repository to upgrade KDE from 4.4.2 to 4.4.5, you might find many KDE packages with multiple versions. 

If you are using KDE 4.4.5, then it would be better to install 4.4.5 version of Kbreakout. (Most KDE applications carry the same version as the version of desktop they were meant for.)

Hope this helps.

Thanks very much.  Just what I was after :D

---

### Post by SeijiSensei on 2011-03-27
I'd check /etc/apt/sources.list as well to make sure you don't have duplicate repositories from different Ubuntu versions.  If you're using Lucid, make sure you only have Lucid repositories in the list.

---

### Post by AnotherMuggle on 2011-03-27
> **SeijiSensei said:**
> I'd check /etc/apt/sources.list as well to make sure you don't have duplicate repositories from different Ubuntu versions.  If you're using Lucid, make sure you only have Lucid repositories in the list.

Thanks for the advise, I've reviewed the file and everything looks good.

---

