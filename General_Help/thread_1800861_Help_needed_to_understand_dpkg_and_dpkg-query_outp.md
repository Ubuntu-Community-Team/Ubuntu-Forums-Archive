---
title: "Help needed to understand dpkg and dpkg-query output"
date: 2011-07-09
forum: General Help
---

### Post by ianc1 on 2011-07-09
Hi

I am writing a script to check whether a list of packages is installed and if not to install them.  I intend to use this at future installs and have no problem with the script. However, I am confused by the outputs of dpkg and dpkg-query.  Using the package "cheese" as an example I get the following:

```
dpkg-query -l cheese
No packages found matching cheese.

dpkg -s cheese
Package `cheese' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
```I read this as cheese is not installed but the machine has no access to its package due to the lack of info.  This is odd as the output of apt-cache show provides me with all the info:

```
apt-cache show cheese
Package: cheese
Priority: optional
Section: gnome
Installed-Size: 260
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Architecture: i386
Version: 2.32.0-0ubuntu2
.....
```These outputs confuse me.  Can anyone shed some light on their discrepancies.

Thanks

---

### Post by matt_symes on 2011-07-09
Hi

From [http://en.wikipedia.org/wiki/Dpkg](http://en.wikipedia.org/wiki/Dpkg)

> **dpkg** is the [software]("http://en.wikipedia.org/wiki/Software") at the base of the [Debian]("http://en.wikipedia.org/wiki/Debian") [package management system]("http://en.wikipedia.org/wiki/Package_management_system"). dpkg is used to install, remove, and provide information about [.deb]("http://en.wikipedia.org/wiki/Deb_%28file_format%29") [packages]("http://en.wikipedia.org/wiki/Software_package_%28installation%29"). > higher level tools, such as [APT]("http://en.wikipedia.org/wiki/Advanced_Packaging_Tool"), are used to fetch packages from remote locations or deal with complex package relations. dpkg-query shows you what is installed on your system. dpkg is used to install applications on your system.

Apt is used to download packages from the repositories defined in your sources.list and sources.d/* directory.

The apt-cache command is used to query the database of installable packages and dpkg-query is used to query the installed packages.

It's more involved than that but that is essentially it.

Kind regards

---

### Post by ianc1 on 2011-07-09
Many thanks.  I should therefore be using dpkg-query.

If I use this to check status and version using```
dpkg-query -W -f='${Status} ${Version}' package_name
```Using cheese as the package outputs:```
No packages found matching cheese.
```and exits with an exit code of 1.

Using gimp as the package outputs:```
unknown ok not-installed 
```and exits with an exit code of 0.

I'm lost here.  Neither package is installed but the results so not match?

Any ideas?

---

### Post by matt_symes on 2011-07-09
Hi

Have you ever had the gimp installed on your PC and then uninstalled it ?

Kind regards

---

### Post by ianc1 on 2011-07-09
Yes, but I did a reinstall of the distro two days ago.  I therefore have a pretty much virgin machine.  On my previous install I also got these results which to me seem irregular.

Thanks

---

### Post by matt_symes on 2011-07-09
Hi

That is pretty inconsistent behaviour using dpkg-query.

In bash a return value of zero is success so dpkg-query is finding the package gimp and returning success even though it is not installed.

When it cannot find the package at all it returns 1 (failure).

I guess the gimp must be in the dpkg package database when Ubuntu is first installed even if it is not installed.

You could try something like this

```
matthew@matthew-laptop:/var/lib/dpkg$ dpkg-query -W -f='${Status} ${Version}' libdvdcss2
install ok not-installed 
matthew@matthew-laptop:dpkg -l | grep libdvdcss2
matthew@matthew-laptop:/var/lib/dpkg$ echo "$?"
1
matthew@matthew-laptop:/var/lib/dpkg$ dpkg -l | grep rfkill
ii  rfkill                                0.3-3                                           tool for enabling and disabling wireless dev
matthew@matthew-laptop:/var/lib/dpkg$ echo "$?"
0
matthew@matthew-laptop:/var/lib/dpkg$
```Kind regards

---

### Post by ianc1 on 2011-07-11
Thanks for that suggestion.  I thought```
dpkg -l package
```was basically doing the same as```
dpkg -l | grep package
```but this is obviously not the case.

I suppose script wise a quicker way to do this would be to load the output from dpkg -l into a variable and search this for each package rather than running dpkg-l for every individual package.

Since starting this thread I have found another alternative way of doing this using```
apt-cache policy package
```If the package is not installed the second line of the output reads:```
Installed: (none)
```Thanks for your help, whilst I am still confused by the outputs of dpkg and dpkg for some of the packages which are not installed I think the problem is essential solved via your proposed work around.

Thanks again.

---

### Post by matt_symes on 2011-07-11
Hi
> 
Thanks for that suggestion. 

I thought   
     ```
dpkg -l package
```was basically doing the same as 
    ```
 dpkg -l | grep package 
```but this is obviously not the case.The difference between these two is as the output of dpkg is being piped into the grep command, it is the grep command that is succeeding or failing unlike the first one where dpkg is succeeding or failing.

You are looking to see if the package is installed and not the command succeeding or failing and that is where, i think, most of the confusion is from.

I think some of the commands have different semantic ideas of what constitutes failure or success.

I must admit, i was very surprised to see gimp in dpkg's database after it had never been installed.

Kind regards.

---

