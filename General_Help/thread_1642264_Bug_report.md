---
title: "Bug report"
date: 2010-12-10
forum: General Help
---

### Post by Pollyanna1 on 2010-12-10
I am not sure where to report bug, but any ways I will put it here and admin can move it.

When I upgrade my ubuntu 10.04 to 10.10 it shows me this message and I have no idea what is that about. Just to help ubuntu to fix if that the case.


=======
Could not install '/var/cache/apt/archives/python-freevo_1.9.0-5ubuntu1_all.deb'

The upgrade will continue but the '/var/cache/apt/archives/python-freevo_1.9.0-5ubuntu1_all.deb' package may not be in a working state. Please consider submitting a bug report about it.

subprocess new pre-installation script returned error exit status 1

========

---

### Post by sikander3786 on 2010-12-10
Bugs need to be filed at Launchpad.

[https://www.launchpad.net](https://www.launchpad.net)

Instead, we can try to work on and correct that error.

Applications > Accessories > Terminal:

Post the output of this command.

```
sudo apt-get update && sudo apt-get upgrade
```

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by mick222 on 2010-12-10
After the upgrade is it not possible to just reinstall freevo

---

