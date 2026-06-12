---
title: "Which flash plugin should I install?"
date: 2010-06-10
forum: General Help
---

### Post by inameiname on 2010-06-10
What is the difference between adobe-flashplugin, flashplugin-installer, and flashplugin-nonfree? All the versions in my repos are the same: 10.1.53.64. 

Which should I choose, or are they all the same in the end?

---

### Post by clhsharky on 2010-06-11
inameiname

When I install ubuntu-restricted-extras I get flashplugin-installer installed. I have had no issues with flash on my hardware with this installation.

Sharky

---

### Post by James78 on 2010-06-11
Flashplugin-installer is the default, flashplugin-nonfree is a transitional package, and adobe-flashplugin is... Well, it doesn't even exist in the Lucid repo's as far as I can see.

So basically, you should install flashplugin-installer.

---

### Post by inameiname on 2010-06-11
Thanks for the input. I had flashplugin-installer already installed, as well as ubuntu-restricted-extras, and noticed it was the latest as well from my repos. I was just curious.

FYI, adobe-flashplugin is in the canonical repo, and it's the latest release, as of today:

[http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages

---

### Post by lovinglinux on 2010-06-11
> **inameiname said:**
> Thanks for the input. I had flashplugin-installer already installed, as well as ubuntu-restricted-extras, and noticed it was the latest as well from my repos. I was just curious.

FYI, adobe-flashplugin is in the canonical repo, and it's the latest release, as of today:

[http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages

Version 10.1 is not showing in my repos, which still has version 10.0.45.2. I have the partner repository enabled and I'm using an up to date mirror.

---

### Post by inameiname on 2010-06-11
Hmmm, I don't know why.

Here is my terminal output, using apt-policy:

aptpolicy adobe-flashplugin
[sudo] password for me: 
adobe-flashplugin:
  Installed: (none)
  Candidate: 10.1.53.64-1lucid1
  Version table:
     10.1.53.64-1lucid1 0
        500 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages
        500 [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Packages

aptpolicy flashplugin-installer
flashplugin-installer:
  Installed: 10.1.53.64ubuntu1
  Candidate: 10.1.53.64ubuntu1
  Version table:
 *** 10.1.53.64ubuntu1 0
        500 [http://ppa.launchpad.net/guido-iodice/guiodiclucid/ubuntu/](http://ppa.launchpad.net/guido-iodice/guiodiclucid/ubuntu/) lucid/main Packages
        100 /var/lib/dpkg/status
     10.1.53.64ubuntu0.10.04.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Packages
     10.0.45.2ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Packages

aptpolicy flashplugin-nonfree
flashplugin-nonfree:
  Installed: (none)
  Candidate: 10.1.53.64ubuntu1
  Version table:
     10.1.53.64ubuntu1 0
        500 [http://ppa.launchpad.net/guido-iodice/guiodiclucid/ubuntu/](http://ppa.launchpad.net/guido-iodice/guiodiclucid/ubuntu/) lucid/main Packages
     10.1.53.64ubuntu0.10.04.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Packages
     10.0.45.2ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Packages

FYI, here is the link that got me on this in the first place:

[http://www.webupd8.org/2010/06/adobe-flash-player-101-uploaded-to.html](http://www.webupd8.org/2010/06/adobe-flash-player-101-uploaded-to.html)
[http://www.webupd8.org/2010/06/adobe-flash-player-101-finally-released.html](http://www.webupd8.org/2010/06/adobe-flash-player-101-finally-released.html)

---

### Post by lovinglinux on 2010-06-11
It's available now.

---

### Post by inameiname on 2010-06-11
Ah, ok, cool.

---

### Post by quirkification on 2010-06-11
Anyone have any advice for 1080p lagging?
Everything else is fine, but 1080p doesn't play right.

and this is only on google chrome, firefox is fine.

---

