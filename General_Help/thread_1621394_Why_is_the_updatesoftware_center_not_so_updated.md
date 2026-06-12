---
title: "Why is the update/software center not so updated?"
date: 2010-11-14
forum: General Help
---

### Post by leon_chame on 2010-11-14
I'm just curious... I have filled up my computer with software via the software center because it was so easy...and I update my computer fully every time asked...even check the repositories from time to time...I have been waiting for lots of my software to update to more current version even though I have been hitting more and more a need to download and install manually because I need more modern versions....seriously lots of them are a year or more behind?

Is there a reason for this I havent found so far? or a way to find non-canonical repository list to use software center?

btw some of the most important software to me is:

virtualbox ose
java
eclipse
tomcat

all of these are seriously out of date and never updated...:( why?

thanks in advance!

---

### Post by Monotoko on 2010-11-14
Generally updates for packages like that do not come until the next Ubuntu version. If you update to 10.10 you will have the most up-to-date versions. The fixes that come with the update manager are for system software and security patches.

---

### Post by snowpine on 2010-11-14
Your Ubuntu version number will tell you approximately how old the applications in the repository are. For example if you are using 8.04, your applications will be the stable versions from April (4th month) 2008, if you're using 10.10, your apps are from October (10th month) 2010, and so forth. This is because Ubuntu develops "stable" releases (not "rolling release" like a distro such as Arch Linux).

You are of course free to install newer versions of applications from other, unsupported sources if you choose. For example you can always find the latest Virtualbox at [virtualbox.org]("http://virtualbox.org").

---

### Post by leon_chame on 2010-11-14
Thank you both for the replies so far.  Can I ask where you got your information from so I read up about it.  I'm still a little confused to as to 'why' and how to plan for things to install and maintain and I guess what is deemed system software.

For example what is labled stable is only labeled stable for the distro but not the use...for ex, the vbox version is not stable or usable for even ubuntu 10.10, win7, or fedora 13 if you want to use their guest editions...(unless you hack them up )?

The python runtime is updated but not the java?  Firefox is updated automatically but not skype, Geany (not system but perhaps because of gedit?) is automatically updated but not Eclipse (which btw is hardly a stable version with open jdk) and so on....?

Thanks again!

---

### Post by mcduck on 2010-11-14
In this case the "stable" version means the version which was available at the time when your Ubuntu release was in development. The most stable version Ubuntu developers were able to test together with all the other packages.

The basic rule is that the package versions are all locked after the version freeze, near the end of the relese's development cycle. After that they are only updated for security reasons and to fix serious bugs (serious as in "might destroy user data" etc).

There are some exceptions to the rule, at least Firefox is kept up-to-date in new Ubuntu releases. And if a package has fairly few dependencies (updating it is unlikely to cause problems with other packages) it might be backported from current development release. You need to enable the "backports" repository in software sources if you wish to get backport updates.

Other than that, if you wish to always have the latest-and-greatest version of some program you need to use some 3rd-party repository. You should be able to find a PPA repository with new packages for almost any commonly used application.

And of course there's always the option of using some Linux distro with rolling-release system if you prefer bleeding edge packages over tested versions.

edit: You can read more about Ubuntu's development process here:
[https://wiki.ubuntu.com/UbuntuDevelopment/ReleaseProcess]("https://wiki.ubuntu.com/UbuntuDevelopment/ReleaseProcess")
[https://wiki.ubuntu.com/TimeBasedReleases]("https://wiki.ubuntu.com/TimeBasedReleases")

> 
What kind of changes are appropriate to make in a released version of Ubuntu?

We only update packages for specific types of changes:

    * Fixes for security vulnerabilities
    * Other high-impact bug fixes, for example those which cause data loss
    * Very conservative, unintrusive bug fixes with substantial benefit and very low risk 


---

### Post by leon_chame on 2010-11-14
thanks Duck!! That explains it quite well and helps lots!

---

