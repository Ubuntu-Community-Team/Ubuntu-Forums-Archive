---
title: "Questions about dependency issues and package installation"
date: 2010-01-20
forum: General Help
---

### Post by blueshiftoverwatch on 2010-01-20
A new stable version of BOINC has been out for two months now and the updated package isn't in the Ubuntu repos yet. Not being completely up to date normally isn't a huge deal. But the new version of BOINC utilizes your GPU to help speed up calculating data units. While the version in the Ubuntu repos doesn't.

So I'm trying various ways to get the new version of the package.

First I tried to compile from the source code. So I used subversion to download the code and selected the "_autosetup" file from it. During the ./configure stage it tells me that I can't install the package until I install OpenSSL. But OpenSSL is already installed.

Then I download the Debian binaries from Debian.org. But I can't install it because it tells me I need libssl0.9.8. So I go into Synaptic and see that it's already installed. I went to Debian.org yet again and download their version of libssl0.9.8. It tells me I can't install the package because a **later** version of the same package is already installed.

You can download the BOINC client and manager in an .sh file for use on any Linux distro. But that only unpackages the file in your /home. Which doesn't seem like the proper way to install a package. I don't want my /home being full of packages. That's what the various folders in / are for.

My questions:

1. Why do these packages fail to detect that the dependencies they require are already installed? Is it because Ubuntu installs them in places where the package/source doesn't expect them to be? If yes, why does Ubuntu go against the grain and install things in non-default places?

2. On a scale of 1-10 (10 = extremely dangerous ; 1 = completely safe) how dangerous is it to install packages from Debian.org on Ubuntu? I've heard that 90% of the time nothing bad will happen. But they're not 100% compatible and can possibly cause problems.

3. Why do so many applications for Linux not come in the form of precompiled binaries? I couldn't find a single website that carries binaries for BOINC. Which, you would think would be a popular enough project to warrant them.

4. What's the deal with .sh files? When you install an application the actual application data files are supposted to be in the various subdirectories of / and only the settings and other userdata is stored in /home. Why would anyone want to run an **entire** application out of their /home? I've noticed that Google Earth does this as well, which annoys me.

---

### Post by blueshiftoverwatch on 2010-01-21
Anyone?

---

### Post by happyhamster on 2010-01-21
> **blueshiftoverwatch said:**
> 
1. Why do these packages fail to detect that the dependencies they require are already installed? Is it because Ubuntu installs them in places where the package/source doesn't expect them to be? If yes, why does Ubuntu go against the grain and install things in non-default places?
It's likely because the correct package isn't installed. In this case it probably needs some development file (a .dev file). If I would have to guess; probably libcurl4-openssl-dev

One way of pulling in dependencies for compilation is having boinc and boinc-dev installed from the repos, and run:

sudo apt-get build-dep boinc

> 
2. On a scale of 1-10 (10 = extremely dangerous ; 1 = completely safe) how dangerous is it to install packages from Debian.org on Ubuntu? I've heard that 90% of the time nothing bad will happen. But they're not 100% compatible and can possibly cause problems.
Depends on how far you're pushing things. Installing some self-contained package is safe. Installing a package that relies on other Debian packages should be safe as long as there aren't any conflicts with existing ubuntu packages. Everything else is potentially dangerous (forcing installs, creating symlinks manually, etc). You could end up with a half-upgraded unstable system. And you'll make your package manager cry, which is just not cool :)

> 
3. Why do so many applications for Linux not come in the form of precompiled binaries? I couldn't find a single website that carries binaries for BOINC. Which, you would think would be a popular enough project to warrant them.

Because there are many linux distros, and they do things slightly differently. There are also several hardware architectures to consider (AMD64, i386, etc). It's hard work to create packages for all such combinations. The distros themselves will usually do a better job too (taking care of integrating the application in the desktop environment, perhaps applying security policies, etc).

> 4. What's the deal with .sh files? When you install an application the actual application data files are supposted to be in the various subdirectories of / and only the settings and other userdata is stored in /home. Why would anyone want to run an **entire** application out of their /home? I've noticed that Google Earth does this as well, which annoys me.
That's just a shell script. It can be and do anything. In this case it just puts files in the correct relative paths I assume. You could probably move all those files and folders somewhere else. For example: create a hidden folder .boinc and move it all there. It might still work and it won't show up in your file browser.

I think installing packages like this is pretty nice: it avoids invoking root privileges, which somewhat counters the drawbacks of installing third-party non-repository stuff on linux.

[edit: typos]

---

### Post by happyhamster on 2010-01-21
> **happyhamster said:**
> You could probably move all those files and folders somewhere else. For example: create a hidden folder .boinc and move it all there. It might still work and it won't show up in your file browser.
Just remembered that a smarter way of doing this (it won't require moving stuff), is creating a text file called ".hidden" in your home folder and add the name of the folder you want to be invisible.

---

### Post by blueshiftoverwatch on 2010-01-22
> **happyhamster said:**
> It's likely because the correct package isn't installed. In this case it probably needs some development file (a .dev file). If I would have to guess; probably libcurl4-openssl-dev

One way of pulling in dependencies for compilation is having boinc and boinc-dev installed from the repos, and run:

sudo apt-get build-dep boinc
I tried that, but encountered the same error.
> **happyhamster said:**
> That's just a shell script. It can be and do anything. In this case it just puts files in the correct relative paths I assume. You could probably move all those files and folders somewhere else. For example: create a hidden folder .boinc and move it all there. It might still work and it won't show up in your file browser.
It's just a psychological thing where I don't like the idea of entire applications being stored in /home. Even if it's a hidden folder.

Thanks for the responces.

---

### Post by ankspo71 on 2010-01-22
Hi,
If you were to download GoogleEarthLinux.xx.xx.bin from the website, you can install it as 'sudo' to install it to the system directories, but if you install it as non-sudo it will install to the /home directory.

bash GoogleEarthLinux.xx.xx.bin = /home
sudo bash GoogleEarthLinux.xx.xx.bin = /

I don't know why this is, but it's something I've noticed.

---

### Post by blueshiftoverwatch on 2010-02-06
> **blueshiftoverwatch said:**
> During the ./configure stage it tells me that I can't install the package until I install OpenSSL. But OpenSSL is already installed.
I was talking to an ex-Ubuntuer who now uses OpenSUSE who said that other distros, especially the lighter ones like Slackware are much better at detecting already existing dependencies when installing non-official software, like source code compiles and binary packages. Is there any truth to this?
> **ankspo71 said:**
> Hi,
If you were to download GoogleEarthLinux.xx.xx.bin from the website, you can install it as 'sudo' to install it to the system directories, but if you install it as non-sudo it will install to the /home directory.
I'm probably going to do a fresh install when Lucid Lynx comes out in April. I'll give that a try then.

---

### Post by andrew.46 on 2010-02-06
Hi blue,

> **blueshiftoverwatch said:**
> I was talking to an ex-Ubuntuer who now uses OpenSUSE who said that other distros, especially the lighter ones like Slackware are much better at detecting already existing dependencies when installing non-official software, like source code compiles and binary packages. Is there any truth to this?

This is partly true :). Slackware does not 'detect' dependencies as such as there is no dependency checking in Slackware. However Slackware is a superb compiling environment because packages are not split up (there are no -dev files) and if a *full* installation is done with Slackware many compiling dependencies are met 'out of the box'. The rest of course have to be chased down by hand but this is surprisingly easy...

All the best,

Andrew

---

### Post by blueshiftoverwatch on 2010-02-07
> **andrew.46 said:**
> This is partly true :). Slackware does not 'detect' dependencies as such as there is no dependency checking in Slackware. However Slackware is a superb compiling environment because packages are not split up (there are no -dev files) and if a *full* installation is done with Slackware many compiling dependencies are met 'out of the box'. The rest of course have to be chased down by hand but this is surprisingly easy...
This is interesting. Do you know of any good articles that go into further detail?

---

### Post by andrew.46 on 2010-02-10
Hi blueshift,

> **blueshiftoverwatch said:**
> This is interesting. Do you know of any good articles that go into further detail?

There are many such articles but a decent exposition of the package management tools available to slackware can be seen here:

Chapter 18 Slackware Package Management
[http://www.slackbook.org/html/package-management.html](http://www.slackbook.org/html/package-management.html)

All the best,

Andrew

---

### Post by blueshiftoverwatch on 2010-03-07
> **blueshiftoverwatch said:**
> 2. On a scale of 1-10 (10 = extremely dangerous ; 1 = completely safe) how dangerous is it to install packages from Debian.org on Ubuntu? I've heard that 90% of the time nothing bad will happen. But they're not 100% compatible and can possibly cause problems
> **happyhamster said:**
> Depends on how far you're pushing things. Installing some self-contained package is safe. Installing a package that relies on other Debian packages should be safe as long as there aren't any conflicts with existing ubuntu packages. Everything else is potentially dangerous (forcing installs, creating symlinks manually, etc). You could end up with a half-upgraded unstable system. And you'll make your package manager cry, which is just not cool :)
I was just thinking that maybe the solution to this problem would be to use Debian instead of Ubuntu. It seems like the Debian repositories are much larger than Ubuntu's and that whenever I have a package that requires certain dependencies, Debian's website almost always has them while Ubuntu's doesn't. Or the Debian dependencies when installed instead of the Ubuntu ones seems to solve my issues.

---

