---
title: "Is there a way to prevent a package from being installed?"
date: 2012-01-13
forum: General Help
---

### Post by Gen2ly on 2012-01-13
I'd like to be able to prevent a package from being installed.  A certain package is causing problems on my system so I was wondering if there is possibly a way to block a package (to be able to prevent its' installation).  Has anybody heard of anything like this?

---

### Post by kc1di on 2012-01-13
> **Gen2ly said:**
> I'd like to be able to prevent a package from being installed.  A certain package is causing problems on my system so I was wondering if there is possibly a way to block a package (to be able to prevent its' installation).  Has anybody heard of anything like this?

There are ways to do that but a little more info needed here. Are you talking about a package being install by default when you install Ubuntu or one being updated in synaptic?  The procedure is different for each.

---

### Post by Gen2ly on 2012-01-13
I *need* to do this for new package.  I do know about holding select packages but this is a program that might regularly be installed freshly by someone and it would be nice to prevent getting installed anew.

---

### Post by Gen2ly on 2012-01-13
bump

---

### Post by lynrock on 2012-01-14
If you use Synaptic there is an option: Packages > Lock version. I've only ever used this to prevent an installed package from upgrading but from a quick trial it does seem to work on a package that is not installed and prevent it from installing.

---

### Post by Gen2ly on 2012-01-14
> **lynrock said:**
> If you use Synaptic there is an option: Packages > Lock version. I've only ever used this to prevent an installed package from upgrading but from a quick trial it does seem to work on a package that is not installed and prevent it from installing.

There is a way to "hold" a package:

```
echo <package name> hold | sudo dpkg --set-selections
```

Unfortunately this solution via Synaptic seems to replicate the same behavior, i.e. I'm still able to run **sudo apt-get install <package>** from the command line and install the package.

Good try though.  Any other ideas?

---

### Post by Gen2ly on 2012-01-16
Looked some in the past couple days and wasn't able to find anything.  Figuring there is no way for this to be done.

---

### Post by pbrane on 2012-01-16
> **Gen2ly said:**
> Looked some in the past couple days and wasn't able to find anything.  Figuring there is no way for this to be done.

Maybe this will help.
[http://www.codealpha.net/737/how-to-restrict-a-specific-package-from-installing-apt-pinning/]("http://www.codealpha.net/737/how-to-restrict-a-specific-package-from-installing-apt-pinning/")

---

### Post by Zill on 2012-01-16
> **Gen2ly said:**
> I *need* to do this for new package.  I do know about holding select packages but this is a program that might regularly be installed freshly by someone and it would be nice to prevent getting installed anew.
You *could* use package locking or apt pinning but any user who has admin rights can simply use sudo or gksudo to overcome this.

Why not simply restrict admin rights to the users you *trust* to install the right software (possibly just yourself)?

---

### Post by imachavel on 2012-01-16
I mean cmon, synaptic package manager clearly has the package>
mark for removal
mark for complete removal
lock

also in settings you can click the option to mark changes that will effect other packages

but you have not been clear as was requested, we would all need a lot more information about which package you don't want installed. is it an update? Something to remove completely? You can right click on it and choose to un install the package if you want. Otherwise what else can be said without more information. 

[http://www.addictivetips.com/ubuntu-linux-tips/how-to-completely-uninstall-packages-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-completely-uninstall-packages-in-ubuntu-linux/)

---

### Post by imachavel on 2012-01-16
> **Zill said:**
> You *could* use package locking or apt pinning but any user who has admin rights can simply use sudo or gksudo to overcome this.

Why not simply restrict admin rights to the users you *trust* to install the right software (possibly just yourself)?

that would work but I don't think it was specified that this was exactly what he wanted. Of course why not.

---

### Post by dcstar on 2012-01-18
> **Gen2ly said:**
> I *need* to do this for new package.  I do know about holding select packages but this is a program ***that might regularly be installed freshly by someone*** and it would be nice to prevent getting installed anew.

Don't give any users admin rights then they cannot install packages.

---

### Post by Gen2ly on 2012-02-03
> **pbrane said:**
> Maybe this will help.
[http://www.codealpha.net/737/how-to-restrict-a-specific-package-from-installing-apt-pinning/]("http://www.codealpha.net/737/how-to-restrict-a-specific-package-from-installing-apt-pinning/")

Ah, ha!  This is exactly what I was looking for!

> **imachavel said:**
> ... synaptic package manager... has[:]
mark for removal
mark for complete removal
lock

...

but you have not been clear as was requested... is it an update? Something to remove completely? You can right click on it and choose to un install the package if you want...

My apologies imachavel.  Perhaps I should have been more clear.  pbrane was right though to figure that I want to *prevent* a certain new package install.

Apt pinning/locking works to prevent a regular package installation method and is good enough for my needs.

Appreciate the help guys.

---

