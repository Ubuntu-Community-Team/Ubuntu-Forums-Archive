---
title: "admin privileges"
date: 2010-05-08
forum: General Help
---

### Post by simon dew on 2010-05-08
Ive re installed Xubuntu 9.10 after a disastrous dalliance with 10.04 both Xubuntu and Ubuntu net-book version. I have a 4GB Asus Eee and because of the hard drive restrictions of 4gb I run the OS on an SD flash card of 16GB. This I believe has been the problem with the later systems. Anyway I'm now trying to access the 4gb hardwired storage chip in the Eee and to do so I downloaded KDE Partition Manager. This won't allow me to use it as it says I dont have admin privileges but I'm unable to log in a root as it rejects my password. Suggestions welcome.
Cheers Simon

---

### Post by michael_schmid on 2010-05-08
From the shell of your choice, try

```
sudo kpartitionmanager
```

At the passwort prompt, enter the login password of your user account. The root account by default is disabled in Ubuntu for security reasons, all administrative work can be done by *pretending* to be root (using "sudo").
Try "man sudo" for further information.

---

### Post by lisati on 2010-05-08
Also see here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by simon dew on 2010-05-08
Brill thanks for all the help I'm sorted. Back with fully functional 9.10! Cheers Simon

---

