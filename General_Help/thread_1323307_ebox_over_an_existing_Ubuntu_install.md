---
title: "ebox over an existing Ubuntu install"
date: 2009-11-11
forum: General Help
---

### Post by memilanuk on 2009-11-11
Hello,

How many out there are using ebox over an existing Ubuntu installation, vs. a complete ebox install from scratch?  Have you gone through and culled out unused modules, or did you select only specific ones during initial install? And finally...

...do you feel ebox restricts your options in *manually* configuring your system later?

---

### Post by foolano on 2009-11-12
A complete eBox install is faster because it includes all the dependencies and pre-seed most of the debconf questions that otherwise would be asked by each individual dependency package.

eBox will warn you if it needs to overwrite a configuration file that has been modified manually. You can also use its hooks to customize configuration options.

The answer you need to ask yourself is if eBox gives you the functionality you need :)

---

