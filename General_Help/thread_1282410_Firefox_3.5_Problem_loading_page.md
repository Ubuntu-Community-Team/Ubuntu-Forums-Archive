---
title: "Firefox 3.5: Problem loading page"
date: 2009-10-04
forum: General Help
---

### Post by crispygoat on 2009-10-04
Since I upgraded to Firefox 3.5 using ubuntuzilla, I can't get any pages to load. It always says "Problem Loading Page" Firefox can't find the server at x. The internet connection works as I can use other browsers.

Thanks

---

### Post by twright on 2009-10-04
Are you on 64bit Ubuntu - I have seen this problem before when using 32bit firefox 3.5 on it.

Otherwise it might be best just to wait or install the [firefox-3.5]("apt:firefox-3.5") package from the repos - Ubuntu Karmic along with 3.5 is coming out in less than a month anyway.

---

### Post by crispygoat on 2009-10-04
I'm not sure which version of Ubuntu I got. I used KDE for a while, until I couldn't stand its buggyness and re installed Ubuntu 9.04 from a disc I got a while ago.. can't remember if it was 64 bit or 32..

---

### Post by lovinglinux on 2009-10-04
See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

---

### Post by nanotube on 2009-10-05
> **crispygoat said:**
> Since I upgraded to Firefox 3.5 using ubuntuzilla, I can't get any pages to load. It always says "Problem Loading Page" Firefox can't find the server at x. The internet connection works as I can use other browsers.

Thanks

if you're on ubuntu64bit, that's a known problem - check out ubuntuzilla faq for a fix.

---

### Post by twright on 2009-10-05
I would just completely remove ubuntuzilla etc and install the version of firefox 3.5 which is in the repositories otherwise you will probably have problems in less then a month when the next version of Ubuntu comes out (including firefox 3.5 by default).

---

### Post by lovinglinux on 2009-10-05
> **twright said:**
> I would just completely remove ubuntuzilla etc and install the version of firefox 3.5 which is in the repositories otherwise you will probably have problems in less then a month when the next version of Ubuntu comes out (including firefox 3.5 by default).

You will probably have issues when Karmic comes out, if you install from the repositories. The Ubuntuzilla version uses the same Firefox profile folder (~/.mozilla/firefox) as the default FF 3.0 installation and as probably will do Karmic, while the version from the repositories uses a different folder (~/mozilla/firefox-3.5) and makes a copy of your current profiles into it. So initially the profiles are the same, but after you start using Shiretoko 3.5, it's profile will not be in sync with the one used by FF 3.0.

I bet when Karmic comes out there will be tons of threads from people freaking out because Firefox will use their old profiles, not the one used by Shiretoko. They will think they have lost their bookmarks and other settings.

So I recommend Ubuntuzilla instead. Just uninstall it before upgrading to Karmic to be safe. Firefox 3.5 from Karmic will then use your current profile.

---

### Post by twright on 2009-10-05
> **lovinglinux said:**
> 
I bet when Karmic comes out there will be tons of threads from people freaking out because Firefox will use their old profiles, not the one used by Shiretoko. They will think they have lost their bookmarks and other settings.

Actually Karmic uses an updated version of the same package by default, there should be no issues updating it - It Should Just Work.
```

Package: firefox-3.5
Priority: optional
Section: web
Installed-Size: 3676
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Architecture: i386
Version: 3.5.3+build1+nobinonly-0ubuntu3
**Replaces: firefox-3.0, firefox-3.1**
Provides: firefox-3.1, www-browser
Depends: fontconfig, psmisc, debianutils (>= 1.16), xulrunner-1.9.1 (>= 1.9.1), libasound2 (>> 1.0.18), libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.10), libnspr4-0d (>= 4.7.3-0ubuntu1~), libpango1.0-0 (>= 1.14.0), libstdc++6 (>= 4.1.1), firefox-3.5-branding | abrowser-3.5-branding
Recommends: ubufox
Suggests: firefox-3.5-gnome-support (= 3.5.3+build1+nobinonly-0ubuntu3), latex-xft-fonts, libthai0
Conflicts: firefox-3.1 (<< 3.1~b4~hg20090317)
Filename: pool/main/f/firefox-3.5/firefox-3.5_3.5.3+build1+nobinonly-0ubuntu3_i386.deb
Size: 965278
MD5sum: ad9b3af977d2e7fbbc34c2c486fa01b5
SHA1: 76a2b3bf147f51c7a5735f09db084e338655cb4b
SHA256: 57fd59d34812c2eb0158757b1f5523c9571e5ff11655bf3abc81e7702bf603dd
Description: safe and easy web browser from Mozilla
 Firefox delivers safe, easy web browsing. A familiar user interface,
 enhanced security features including protection from online identity theft,
 and integrated search let you get the most out of the web.
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Task: ubuntu-desktop, edubuntu-desktop, xubuntu-desktop, mythbuntu-backend-master, mythbuntu-backend-slave, mythbuntu-desktop, mythbuntu-frontend, ubuntu-netbook-remix

```

---

### Post by lovinglinux on 2009-10-05
> **twright said:**
> Actually Karmic uses an updated version of the same package by default, there should be no issues updating it - It Should Just Work.

What I'm saying has nothing to do with the package, but with the profile location.

---

### Post by twright on 2009-10-07
> **lovinglinux said:**
> What I'm saying has nothing to do with the package, but with the profile location.
But seeing how firefox manages profiles it will be migrated automatically (I think) - perhaps I will have to try this out sometime.

---

