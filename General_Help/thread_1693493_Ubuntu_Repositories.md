---
title: "Ubuntu Repositories"
date: 2011-02-22
forum: General Help
---

### Post by steevven1 on 2011-02-22
When using aptitude in 10.04, I notice that I am often not getting up-to-date software. For example, I just did "sudo apt-get install wipe" and I got wipe version 0.21, when the current stable release is 2.1! For Chromium, I got version 9 when the current release is 11!

What's up?

Thank you in advance.

---

### Post by Vaphell on 2011-02-23
just before the release there is a repository freeze to improve stability and help with testing - versions of programs get locked and during lifetime of the release only bugs are fixed, no version changes. To get newer versions of programs you need to jump to newer release, add PPAs (3rd party repositories) for your package manager or install manually.
If you really need newer versions look into PPAs.

e.g. for chromium-daily [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

---

### Post by bhaverkamp on 2011-02-23
Chrome 11 is not the current version that version is in beta. Chrome 9 is the latest stable version and the one your would get from google. This is generally true of all repository items. You are always free setup other repositories and download from them....

---

