---
title: "Can't locate a installed .deb file"
date: 2012-07-25
forum: General Help
---

### Post by uzumakifahim on 2012-07-25
Hi,
I have installed Cinnamon Desktop on system few days before. Now need to get all the .deb files associated with Cinnamon Desktop. I have got all the packages at 

/var/cache/apt/archives

But unfortunately I'm not getting one specific package named "muffin-common". I have confirmed that package is installed perfectly on my system, because Synaptic Package Manager is showing that package as installed.

Here I want to mention another point that, some .deb files of other softwares (like; Firefox, Skype) is not present in that directory. I don't know why it is like this.

Now anyone please help me out, how can I get that .deb file "muffin-common" package. Thanks in advance.

---

### Post by claracc on 2012-07-26
You can look for it through synaptic manager.

You open synaptic package manager, select the program you are looking for, then, click on package, properties and in the windows appearing you select installed files, appearing a list of the programs installed and the place where they are.

---

### Post by uzumakifahim on 2012-07-26
Thanks claracc for your reply. My Synaptic is showing the package (muffin-common) is located at 

/usr/share/doc/muffin-common

But unfortunately there is no .deb file of "muffin-common". In the muffin-common folder of that directory I've found the files below
1. AUTHORS
2.changelog.Debian.gz
3.changelog.gz
4.copyright
5.NEWS.gz
6.README

Please reply so that this problem could be solved ASAP.

---

### Post by asmoore82 on 2012-07-27
The package system does not have to retain the *.deb file after installation.
It's like installing Ubuntu itself from a CD: you don't have to keep the CD in the drive to keep using Ubuntu.

What are you trying to accomplish exactly?

---

### Post by uzumakifahim on 2012-07-27
@asmoore82, actually I am trying to get all the .deb files of Cinnamon Desktop. I need all the .deb files of Cinnamon Desktop and it's dependencies. Cinnamon Desktop is installed on my Ubuntu, but I'm not getting all the .deb, but I need them very urgently. Do you have any idea, where can I get them?

---

### Post by Cheesemill on 2012-07-27
You could always download them again straight from the PPA.
[https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable/+packages](https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable/+packages)

---

### Post by uzumakifahim on 2012-07-27
WOW! [Cheesemill]("http://ubuntuforums.org/member.php?u=559258") really thanks for that. Hope this will works for me. I'll give you the update. 

Thanks again. :)

---

### Post by uzumakifahim on 2012-07-28
Thanks cheesemil again. Your solution works perfect for me. Actually, as far as I remember when I was using Ubuntu 9.04, 9.10; at that time all the .deb files were at /var/cache/apt/archive directory. But now at 12.04 I am not getting all the .debs at that directory. Could you tell me why this is happening now?

---

### Post by NilPointer on 2012-07-28
> **uzumakifahim said:**
> /var/cache/apt/archive
...
But now at 12.04 I am not getting all the .debs at that directory. Could you tell me why this is happening now?


No, it's not supposed to "hold all .deb files". It's cache - just a temporary storage for .debs, downloaded by apt. It's autocleared from time to time.

---

### Post by uzumakifahim on 2012-07-28
Thanks for the information NilPointer.

---

### Post by votsalo on 2012-08-02
You can also try both of:
```
apt-cache showpkg {package}
apt-cache show {package} | grep Filename

```"showpkg" includes something like a url that could point you in the right repository from /etc/apt/sources.list

"show" has a "Filename" line that is the exact filename of the package relative to the root of the repository.

---

