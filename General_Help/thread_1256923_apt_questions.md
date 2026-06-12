---
title: "apt questions"
date: 2009-09-03
forum: General Help
---

### Post by methodtwo on 2009-09-03
If you go about trying to install an application from the source code but later decide to use the repositories however you have installed that application's dependencies from the repos.If you don't do:
```
#apt-get update
```
You will get the same versions of the dependencies when you go ahead and install the application from the repos right?. Or should i uninstall the dependencies before installing the application from the repos?.
The application in question is snort.And the dependencies that i installed from the repos are:
```
libpcap0.8-dev libmysqlclient15-dev mysql-client-5.0 mysql-server-5.0 bison flex apache2 libapache2-mod-php5 php5-gd php5-mysql libphp-adodb php-pear libc6-dev g++ gcc pcregrep libpcre3-dev

```
I just didn't want to end up with a version of snort that didn't know which versions of the dependencies to use.So do i have to uninstall the dependencies before installing snort from the repos?

---

### Post by vedek on 2009-09-03
well when you download a program from the repo it normally downloads all the dependancies so if it detects that you have it, then it won't download it, if you are missing any then it will download the missing ones.

---

### Post by slakkie on 2009-09-03
> **methodtwo said:**
> If you go about trying to install an application from the source code but later decide to use the repositories however you have installed that application's dependencies from the repos.If you don't do:
```
#apt-get update
```
You will get the same versions of the dependencies when you go ahead and install the application from the repos right?. Or should i uninstall the dependencies before installing the application from the repos?.
The application in question is snort.And the dependencies that i installed from the repos are:
```
libpcap0.8-dev libmysqlclient15-dev mysql-client-5.0 mysql-server-5.0 bison flex apache2 libapache2-mod-php5 php5-gd php5-mysql libphp-adodb php-pear libc6-dev g++ gcc pcregrep libpcre3-dev

```
I just didn't want to end up with a version of snort that didn't know which versions of the dependencies to use.So do i have to uninstall the dependencies before installing snort from the repos?

If you install the dependencies manually, it will not remove them if you remove the "main" package.

You install package A, which has dependencies B, C, E it will install B, C and E for you. When you remove A, it will remove B, C and E as well (unless other packages which you installed are dependent on them). If you manually install B, C and E, these will not be removed once A is removed, since you installed them manually.

If you remove the deps now and install snort from the repo's it will install them again and remove them once you remove snort.

---

