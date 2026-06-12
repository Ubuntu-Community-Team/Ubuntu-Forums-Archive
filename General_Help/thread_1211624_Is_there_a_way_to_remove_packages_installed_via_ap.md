---
title: "Is there a way to remove packages installed via apt-get build-dep?"
date: 2009-07-12
forum: General Help
---

### Post by jerome1232 on 2009-07-12
I compiled the latest version of pidgin on my computer and used '**apt-get build-dep pidgin**' to automatically install all the needed dependencies to compile pidgin.

Well now I realized they have a ppa for the version I compiled and have removed my compiled version and installed the ppa version.

I don't like having all those unnecessary packages needed to compile it hanging around, is there a way to have apt-get remove those unnecessary packages?

---

### Post by jerome1232 on 2009-07-14
*bump*

---

### Post by kpkeerthi on 2009-07-14
[https://answers.launchpad.net/apt/+question/8366]("https://answers.launchpad.net/apt/+question/8366")

---

### Post by JohnnySage50307 on 2009-07-14
You could just try
```
sudo apt-get purge [package]
```
 
That will remove the entire package and all configuration files too.
 
As a bit of advice, ALWAYS check your man-pages!

---

### Post by jerome1232 on 2009-07-14
> **kpkeerthi said:**
> [https://answers.launchpad.net/apt/+question/8366]("https://answers.launchpad.net/apt/+question/8366")

Thanks that helps quite a bit actually! Even if it's a painstaking manual process.

edit: Actually the script seems to work great as long as you inspect the list of packages aptitude wants to remove first.

@JohnnySage50307 Actually building a package requires (many in pidgins case) more dependencies than just running it, apt-get purge [packagename] only deals with those runtime dependencies not the build dependencies, but thanks.

---

