---
title: "Difference between Distros and Desktops"
date: 2009-10-14
forum: General Help
---

### Post by wbm on 2009-10-14
Hello,
I have been playing around with Linux on and off for a few years.
Here are a few general questions, as I recently tried out Fedora 11, Suse 11, Mandriva 2009 and of course Ubuntu.
They more or less look all the same to me. What is actually the difference between different distributions?

Desktops:
I understand that there are different desktop environments, and I prefer Gnome. Is there any issue I should be aware of when running KDE applications in Gnome?
What e.g. makes a KDE application a "KDE application" as opposed to a Gnome application? 

Lastly, if I get an external drive, how should it be formatted if I use it just for Linux, or if I want it to be seen on WIndows, Macs and Linux (e.g. a shared folder).
Thanks!!!

---

### Post by doorknob60 on 2009-10-14
> **wbm said:**
> 
Is there any issue I should be aware of when running KDE applications in Gnome? What e.g. makes a KDE application a "KDE application" as opposed to a Gnome application? 

Shouldn't have any real problems. A KDE applications just means it uses the QT toolkit and uses some KDE libraries (as opposed to GTK toolkit and often some Gnome libraries in Gnome apps). Mix and match all you want :)

> **wbm said:**
> 
Lastly, if I get an external drive, how should it be formatted if I use it just for Linux, or if I want it to be seen on WIndows, Macs and Linux (e.g. a shared folder).
Thanks!!!
If you plan on only using it for Linux, EXT3 (or EXT4) would be good. If you want it to work on any OS, FAT32 is the best choice.

---

### Post by falconindy on 2009-10-14
> **wbm said:**
> I understand that there are different desktop environments, and I prefer Gnome. Is there any issue I should be aware of when running KDE applications in Gnome?
What e.g. makes a KDE application a "KDE application" as opposed to a Gnome application?
This is essentially related to the code used to create the GUI. Applications that back up on GTK (Gnome ToolKit) are generally regarded as "Gnome applications", and those that back up on QT are generally regarded as "KDE applications". That doesn't, however, mean that you're limited to running the app on solely that desktop environment. There's plenty of people running K3B (a cd/dvd burning app) on Gnome because it's far better, imo, than Brasero.

> If you plan on only using it for Linux, EXT3 (or EXT4) would be good. If you want it to work on any OS, FAT32 is the best choice.
I disagree. OSX and Linux both have libraries to deal with NTFS, and it's a far superior filesystem compared to FAT32.

---

### Post by jmszr on 2009-10-14
wbm,
> They more or less look all the same to me. What is actually the difference between different distributions?

Hope this helps: [http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions](http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions)

---

### Post by wbm on 2009-10-14
Thanks to all.
I was wondering about NTFS too, as I can already see that from OS X, Windows and Linux on e.g. our File Server at work.
That comparison list is very good, thank you.
I am one of those people running K3B (a cd/dvd burning app) on Gnome btw.

---

### Post by Mighty_Joe on 2009-10-15
> **wbm said:**
> They more or less look all the same to me. What is actually the difference between different distributions?


One big difference between distros is the philosophy: the reason the distro exists.  Ubuntu's [philosophy]("http://www.ubuntu.com/community/ubuntustory/philosophy") is to make software accessible, and it makes some compromises to do that (binary drivers, media codecs).  
Fedora, on the [other hand]("http://fedoraproject.org/wiki/Objectives"), stresses having very up-to-date versions of applications, with an eye to improving [RHEL]("http://en.wikipedia.org/wiki/Red_Hat_Enterprise_Linux").  This is great if you like shiny, but if you don't want the occasional bug, well, maybe it is not for you. Fedora also emphasizes Open Source, so getting media codecs and binary drivers can be more difficult.
[Gentoo]("http://www.gentoo.org/main/en/philosophy.xml") strives for performance and flexibility.  [Slackware's]("http://learn.clemsonlinux.org/wiki/Slackware:Philosophy") goal is stability.
RHEL and Suse, among others, are commercial in nature, so they have tools to make administration easier and institutional support to back you up when you have a problem.  
Some distros are just one guy with an itch to scratch, like [Masonux]("http://sites.google.com/site/masonux/"), a stripped-down Ubuntu that uses the LXDE window manager.
And if you can't find a distro that does what you want, there's a distro [for that]("http://www.linuxfromscratch.org/").

---

