---
title: "how to get list of non installed packages"
date: 2012-04-23
forum: General Help
---

### Post by kev670q on 2012-04-23
Is it possible to get a list of packages that have not been installed yet... I know that dpkg --list will give me a list of installed ones but for instance i know that php can be installed using apt-get install php5-cli... but is it possible to get a list of all these potential packages

---

### Post by houseworkshy on 2012-04-23
Yes the easy way is to use synaptic, in the lower left quarterish  of the screen are various categories, "status" then "uninstalled".

---

### Post by Cheesemill on 2012-04-23
Try:
```
aptitude search php
```You may need to install aptitude first.

---

### Post by kev670q on 2012-04-23
thanks... yeah I need the command line way because I'm using server edition

---

