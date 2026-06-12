---
title: "Local Repository"
date: 2011-03-25
forum: General Help
---

### Post by manishlogan on 2011-03-25
I am running Ubuntu 10.10 as my OS. I also have an .iso file of OpenSuse. It has a lot of packages on it. Can I add it as local repository so that instead of downloading the files from net, if they are available on DVD then I can use them.

---

### Post by ChipOManiac on 2011-03-25
No, not directly... SUSE uses Red Hat Package Manager while Ubuntu is uses Debian Packages... the two are almost the same with a difference of directories...  Therefore you can't install a RPM on a Debian or vice versa...

You can use «alien» to convert the package, but you'll have to do that for each package... enabling the OpenSUSE DVD as a repo won't work since the packages make no sense to Ubuntu whilst in RPM format...

Hope this clarifies everything... :)

---

### Post by manishlogan on 2011-03-25
What if I change all the packages to .deb and then try to add it as repository?

---

### Post by andrewthomas on 2011-03-25
This is going to cause you problems.  

What suse software are you wanting to install that is unavailable in the ubuntu repositories?

---

### Post by ChipOManiac on 2011-03-25
> **manishlogan said:**
> What if I change all the packages to .deb and then try to add it as repository?

That's the point... **converting to .deb has it's problems**, AND you have to convert **each .deb one-by-one**, not very logical... 

just get them off the Ubuntu repo...

---

