---
title: "Software Installation"
date: 2006-03-15
forum: General Help
---

### Post by tstrickland on 2006-03-15
I've just installed Kubuntu and am not familiar with Debian packages (I've been using Mandrake). My attempts to install Debian packages have generally been failures. If Adept or Synaptic can find the right package, it will install it. However, several things I want to install aren't found by these package managers.:( 

I want to install Eric and I've downloaded it as a Debian package and as a tarball. When I doublb-click on the Debian icon for the package, I get an error message in Ark that says, 

[INDENT]"The utility ar is not in your Path. Please install it or contact your system administrator [I don't have one!]"[/INDENT]

I don't know what that means and can't find an "ar" utility.:???: 

If I extract the files from the tarball, the executable files won't run.:???: 

What to do?:cry: 

Thank you!

---

### Post by Xian on 2006-03-15
That application can be installed via Synaptic or APT.
You just need to enable the [extra repositories](https://wiki.ubuntu.com/AddingRepositoriesHowto?).

In this case the package is in the Universe repo.

---

### Post by tstrickland on 2006-03-15
[QUOTE=Xian]That application can be installed via Synaptic or APT.
You just need to enable the [extra repositories](https://wiki.ubuntu.com/AddingRepositoriesHowto?).

In this case the package is in the Universe repo.[/QUOTE]

Thanks! This worked. I had to read very carefully the info on extra repositories that you gave me, but it worked fine!!

---

### Post by nrwilk on 2006-03-15
If, in the future, you find another program which you want and is not in the Repositories, then you can use this command to install it (it does have to be a .deb for this method):
```
sudo dpkg -i <program_name.deb>
```

remember that you must be in the directory where the deb resides in order for the command to see the deb you are referencing.  Else, you must specify the path to it as follows:

```
sudo dpkg -i /home/tstrickland/downloads/<program_name.deb>
```

Hope this helps!  :D

---

