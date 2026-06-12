---
title: "Something about packages (newbie)"
date: 2010-04-11
forum: General Help
---

### Post by mayapower on 2010-04-11
Hi,

I am new to linux and would like to know a few things about packages.
I have developed and application which is based on LSB 4.0.0. Once created, I tested it one freshly installed kubuntu karmic, where no dependency is installed. The main executable was not able to run because it needs LSB core package installed.

Using kPackageKit I installed lsb core 4.0.0 and main app executes with out any problem.

First time when I installed lsb 4.0.0, a huge list of dependencies has shown and those needs to installed along with lsb 4.0.0. To know more about packages I uninstalled lsb 4.0.0 and it was uninstalled very quickly. I did install again and to my surprise, this time there is no window showing the list of dependency, it means that first un installation only removed the lsb core 4.0.0 package.

Why it's like that? Why didn't it un installed the list of dependencies?

Now I know that my app is dependent on lsb core 4.0.0. How do I package it. I never tried this stuff before and I have heard of .deb and .rpm. Which one is to use and why?

lsb core 4.0.0 is available on ubuntu repositories but it may possible that If end user try to install it on a different distro where lsb core is not available then what's is the solution?

Is it possible to create .deb/.rpm package in such a way that it can download the lsb core package from ubuntu repositories? Are there any compatibility issues that may rise when user will install package from other repository? For example user is running fedora or debien or any other distro.

I really apologize if some one finds these questions vague but I am on my way to learning more about linux.

Cheers

Prashant

---

### Post by darolu on 2010-04-11
> I never tried this stuff before and I have heard of .deb and .rpm. Which one is to use and why?
.deb packages are packages designed for Debian and Debian based distributions.
.rpm packages are packages originally designed for Red Hat, it is used by other distros like OpenSuSE too though.

Developers usually release the source code, listing its dependencies on the documentation section (usually a README or INSTALL file or online) or in a configuration script; other people build each distro packages from there. It would be hard (nearly impossible) for a single person to build packages for every distro out there imo; but you can build one for your favourite distro (Ubuntu right?).

Read this thread for more info: [http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003)

> Why didn't it un installed the list of dependencies?
When you uninstall a specific library or application it doesn't uninstall all of its dependencies as they might be used by other applications as well, imagine if uninstalling a gtk based app would uninstall gtk too... (in gnome environments) it wouldn't be nice at all :p

---

