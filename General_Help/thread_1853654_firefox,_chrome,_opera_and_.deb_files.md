---
title: "firefox, chrome, opera and *.deb files"
date: 2011-10-02
forum: General Help
---

### Post by le1 on 2011-10-02
Hey there,

can you please tell me why you can download chrome and opera *.deb files and have it installed on e.g. debian disto in no time but in order to do the same with firefox you have to compile ?

---

### Post by dniMretsaM on 2011-10-02
No, you don't have to compile Firefox. Inside the tarball is a pre-compiled binary, not source code (i.e. no need for ./configure etc). I'm wondering why you don't just install Firefox via the repos or one of the Firefox PPAs (links to Mozilla's PPA's can be found [here](https://launchpad.net/~mozillateam))? Any particular reason? Also, Chromium (Google Chrome is based off of this and they are very, very similar) is available in the repos and PPA's (PPA links [here](https://launchpad.net/chromium-project)).

---

### Post by le1 on 2011-10-03
Well I do know about repositories and I do have the latest and greatest ff on my Ubuntu. I ask because I'm playing with Debian now (since Ubuntu is based on that distro) and wanted to know why can't one just download deb file and install it, why doesn't ff makes it as easy as chrome and opera. Is there any particular reason for that e.g. security or other, just that, curiosity. Also let's just suppose that someone is new to some distro where Chrome is a default web browser, goes to ff site and won't get far from there, it may cause ff to lose some crowd, some not important [**percentage**]("http://www.thetechherald.com/article.php/201140/7678/Google-Chrome-on-track-to-depose-Mozilla-Firefox") but still.

---

### Post by dniMretsaM on 2011-10-03
> **le1 said:**
> Well I do know about repositories and I do have the latest and greatest ff on my Ubuntu. I ask because I'm playing with Debian now (since Ubuntu is based on that distro) and wanted to know why can't one just download deb file and install it, why doesn't ff makes it as easy as chrome and opera. Is there any particular reason for that e.g. security or other, just that, curiosity. Also let's just suppose that someone is new to some distro where Chrome is a default web browser, goes to ff site and won't get far from there, it may cause ff to lose some crowd, some not important [**percentage**]("http://www.thetechherald.com/article.php/201140/7678/Google-Chrome-on-track-to-depose-Mozilla-Firefox") but still.

Debian's Iceweasel is a Firefox derivative that Debian re-branded (you probably already know that though), so that might be what you're looking for. It does have some changes made to it though. And as for why Firefox doesn't distribute .deb packages, it probably has to do with the fact that not every GNU/Linux distribution use the Debian packaging system. There are many others, and Mozilla decided it would be easier to distribute a package that could be used on pretty much all UNIX-like systems, rather than have a package for each different type.

---

### Post by le1 on 2011-10-04
Hey,

but would it be really hard for them do it like

Opera:

Select distribution and vendor:

Arch
CentOS
Debian
Fedora
Gentoo
MEPIS
Mandriva
Mint
Other (DEB)
Other (RPM)
Other (TAR)
PCLinuxOS
RedHat
Sabayon
Slackware
Ubuntu
Xandros - Eee PC Edition
openSUSE

or
Chrome:

32 bit .deb (For Debian/Ubuntu)
64 bit .deb (For Debian/Ubuntu)
32 bit .rpm (For Fedora/openSUSE)
64 bit .rpm (For Fedora/openSUSE)

Or is there anything else that influence their decision ?

---

### Post by WorMzy on 2011-10-04
Software companies are under no obligation to provide various pre-compiled distro-friendly packages, like .debs, .rpms, .tar.xzs, etc.

If you believe that they *should* provide packages like that, contact them and ask them to do so. There's always a chance that they will take your suggestions on board.

---

### Post by lovinglinux on 2011-10-04
I don't know why they don't provide a deb. It would be nice, but the Ubuntu MozillaTeam does a great job packaging Firefox and proving the ppa repositories.

I am not sure if you can install a Firefox deb for Ubuntu on Debian, but you can download them from the ppa archives.

---

### Post by Frogs Hair on 2011-10-04
Opera does provide a .deb package . Select Ubuntu or Debian and choose default package from the drop down menu at the bottom .
[http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

---

### Post by Lars Noodén on 2011-10-04
Opera also has [repository](https://help.ubuntu.com/community/OperaBrowser) that can be used.

---

### Post by mikewhatever on 2011-10-04
> **le1 said:**
> Hey,

but would it be really hard for them do it like

Opera:

Select distribution and vendor:

Arch
CentOS
Debian
Fedora
Gentoo
MEPIS
Mandriva
Mint
Other (DEB)
Other (RPM)
Other (TAR)
PCLinuxOS
RedHat
Sabayon
Slackware
Ubuntu
Xandros - Eee PC Edition
openSUSE

or
Chrome:

32 bit .deb (For Debian/Ubuntu)
64 bit .deb (For Debian/Ubuntu)
32 bit .rpm (For Fedora/openSUSE)
64 bit .rpm (For Fedora/openSUSE)

Or is there anything else that influence their decision ?

Yes, it is hard. Just try compiling something yourself, and you'll see.

While Opera has an impressive assortment of installation packages, with more then 200 active Linux distos, it's easy to find one that's not on the list. Mozilla, provides binaries that don't require installation, and should, theoretically, work on any distro.

---

### Post by dniMretsaM on 2011-10-04
> **le1 said:**
> Hey,

but would it be really hard for them do it like

Opera:

Select distribution and vendor:

Arch
CentOS
Debian
Fedora
Gentoo
MEPIS
Mandriva
Mint
Other (DEB)
Other (RPM)
Other (TAR)
PCLinuxOS
RedHat
Sabayon
Slackware
Ubuntu
Xandros - Eee PC Edition
openSUSE

or
Chrome:

32 bit .deb (For Debian/Ubuntu)
64 bit .deb (For Debian/Ubuntu)
32 bit .rpm (For Fedora/openSUSE)
64 bit .rpm (For Fedora/openSUSE)

Or is there anything else that influence their decision ?

Yes, actually. It would be hard.  If you don't think it would be, try compiling Firefox in 20 different ways and then tell us it's easy. Would it be really convenient? Sure. But personally, I'd prefer Mozilla spend their resources (time, money, employees, etc.) on improving the actual browser, not the packaging. That being said, you could always ask them to start distributing pre-packaged builds. Who knows, they might just start. Heck, if you want to help out your fellow FF users, learn to compile and offer to provide a .deb package for the Debian distribution. They might accept and then you'll be helping your neighbors (which is what free software is all about).

---

