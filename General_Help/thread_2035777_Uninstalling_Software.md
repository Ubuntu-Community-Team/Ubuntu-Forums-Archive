---
title: "Uninstalling Software"
date: 2012-07-31
forum: General Help
---

### Post by jonesyp on 2012-07-31
Hi,

I was just wondering if Linux and Ubuntu in particular worked like MS Windows in terms of when you uninstall programs in Windows, files are often left on the system, and keys in the registry are not removed.  Does Ubuntu fully remove when you use the Apt-Remove commands?

I have noticed that after uninstalling the program icons tend to stay on the Unity Quick Launcher and need to be removed manually.

I have this severe OCD about having a clean system!  You could not imagine the number of times I have re-installed Windows!

Thanks

Peter

---

### Post by raja.genupula on 2012-07-31
Ubuntu have that command too . named as purge . if you want to remove a package and details of it completely from your system then you can use that command.

```
sudo apt-get purge <package_name >
```

or 

```
sudo apt-get remove --purge <pkg-name>
```
for more information you use man page ,
[http://manpages.ubuntu.com/manpages/lucid/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/apt-get.8.html)

---

### Post by jonesyp on 2012-07-31
Thanks for the quick reply.  The question was more about if the apt command completely removed everything, becuase the Windows uninstaller often leaves stuff behind.

Thanks

---

### Post by Frogs Hair on 2012-07-31
The synaptic package manager is a great tool for removing packages and residual packages. Synaptic also displays auto removable packages when an application is removed.

Use caution with this option though and make sure the primary package is removed before marking any thing for removal under auto removable. I have found folders even after running the purge command or complete removal of some applications.

---

### Post by oldos2er on 2012-07-31
> **jonesyp said:**
> Thanks for the quick reply.  The question was more about if the apt command completely removed everything, becuase the Windows uninstaller often leaves stuff behind.

Thanks

Any config files or folders in a user's home folder will be left untouched, so you would need to remove those manually.

---

