---
title: "can't install kdebase-dev"
date: 2006-06-03
forum: General Help
---

### Post by dresnu on 2006-06-03
After upgrading to KDE 3.5.3 I get this when trying to install package kdebase-dev: ```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  kdebase-dev: Depends: kate (= 4:3.5.2-0ubuntu26) but 4:3.5.3-0ubuntu0.1 is to be installed
               Depends: kdesktop (= 4:3.5.2-0ubuntu26) but 4:3.5.3-0ubuntu0.1 is to be installed
               Depends: kicker (= 4:3.5.2-0ubuntu26) but 4:3.5.3-0ubuntu0.1 is to be installed
               Depends: konqueror-nsplugins (= 4:3.5.2-0ubuntu26) but 4:3.5.3-0ubuntu0.1 is to be installed
               Depends: konqueror (= 4:3.5.2-0ubuntu26) but 4:3.5.3-0ubuntu0.1 is to be installed
               Depends: ksysguard (= 4:3.5.2-0ubuntu26) but 4:3.5.3-0ubuntu0.1 is to be installed
               Depends: kwin (= 4:3.5.2-0ubuntu26) but 4:3.5.3-0ubuntu0.1 is to be installed
               Depends: kdelibs4-dev (>= 4:3.5-rc1) but it is not going to be installed
E: Broken packages

```
I'm using Kubuntu Dapper.

**EDIT**: I have also filed a bug here: [https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/48190](https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/48190)

---

### Post by dresnu on 2006-06-05
I tried installing kdebase-dev from aptitude but apart from package kubuntu-desktop it also wants to remove almost all kde programs(!), of course I declined.
This is very annoying because I can't compile anything related to X and kde... :(

---

### Post by w1z4rd on 2006-06-24
[QUOTE=dresnu]I tried installing kdebase-dev from aptitude but apart from package kubuntu-desktop it also wants to remove almost all kde programs(!), of course I declined.
This is very annoying because I can't compile anything related to X and kde... :([/QUOTE]

Im in teh same boat :/ there are a lot of posts about the same thing running around the forums.... anyone out there who can actually help us?

---

### Post by dresnu on 2006-06-25
I solved it using aptitude. Just let it remove everything it wants to. It will fix the problem and install kdebase-dev. After that install kubuntu-desktop again and most of the previously uninstalled packages will be reinstalled. But, before proceeding, I would suggest you write down what packages will be removed because you will probably have to install manually some of them(the ones not included in the standard kubuntu installation[kubuntu-desktop]).

---

