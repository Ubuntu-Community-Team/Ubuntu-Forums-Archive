---
title: "Compiled programs vs packaged programs"
date: 2011-01-01
forum: General Help
---

### Post by mydoghasworms on 2011-01-01
I'm wondering whether, if I want to compile a new version of a program and install it with make install, whether this can interfere with the existing version of the program installed from a package?

In other words, is there a chance I could accidentally overwrite existing binaries from packages with make install? And if I do, what is the best way to recover from that?

---

### Post by GregBrannon on 2011-01-01
Is there a chance that a "manual" install of program might corrupt a previous install from the repositories?  Anything's possible.  You may be able to minimize the chance of that happening by completely understanding the manual install process and then accomplishing it so as to not corrupt existing installs.

A way to recover a repository install after it has been corrupted by any act is to reinstall it.

---

### Post by mydoghasworms on 2011-01-02
Thanks for the reply. What is the best way to go about installing software from source then if you want it to coexist with your existing installed software?
I want to try a newer version of e.g. LMMS than what is in the repository, but am afraid I will do something bad to my existing install.
I have looked at using chroot, but it is quite complicated. Is there perhaps an easy way to set up such an environment, e.g. with a graphical utility?

---

### Post by a-user on 2011-01-02
deinstall the existing one.

additionally you can change the destination directory for your manuall installation if you add the parameter for this to configure befor compiling.
usually you this by ./configure --prefix=/destination-prefix-dir/

---

### Post by oldos2er on 2011-01-02
'make install' should put programs in /usr/local/, so they won't conflict with package-manager-installed programs. At least that's been my, admittedly limited, experience so far.

---

### Post by a-user on 2011-01-04
> **oldos2er said:**
> 'make install' should put programs in /usr/local/, so they won't conflict with package-manager-installed programs. At least that's been my, admittedly limited, experience so far.
many if not most of my packege.manager-installed programs are in /usr/local/

---

### Post by stlsaint on 2011-01-04
> I have looked at using chroot, but it is quite complicated. Is there perhaps an easy way to set up such an environment, e.g. with a graphical utility?

If you do not want to go with chroot than i would next suggest trying out in virtualbox. There is no other "safe" way to test an application in a production environment.

---

