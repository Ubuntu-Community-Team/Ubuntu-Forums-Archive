---
title: "Install Ted in Ubuntu 9.04"
date: 2009-07-07
forum: General Help
---

### Post by moodle on 2009-07-07
Hello,
I'm a Linux and Ubuntu newbie.

I would like to install light word processor Ted.  However, I don't know at all where I should begin. I've found the Ted website ([http://www.nllgg.nl/Ted)]("http://www.nllgg.nl/Ted%29"), and this guide[ http://ubuntuforums.org/showthread.php?t=169574]("http://ubuntuforums.org/showthread.php?t=169574")

However, following the guide, Ted does not come up in the Ubuntu repositories.

A step-by-step guide to installing Ted on Ubuntu would be greatly appreciated.


Thanks in advance for your help,

David

---

### Post by starcraft.man on 2009-07-07
I just had a quick look at the [comparison ]("http://en.wikipedia.org/wiki/Comparison_of_word_processors")to see about TED. I'm pretty disappointed, it lacks many basic features that are expected nowadays.

I would just use abiword (in the repos) if you want a nice stand alone word processor. OpenOffice or Lostus work well enough as suites. I imagine it was removed from the repos for lack of interest by users. You might also want to look up the Koffice suite, but that's more of a KDE application.

As descibed in the tut, you can install it via a terminal (applications > Accessories ) with the following:

```
sudo apt-get install abiword
```

I like it. For more information of install, see my signature guide.

---

### Post by michy99 on 2009-07-07
It seems that TED is no longer in the repositories. The latest package I could find is for Hardy. If you want to download it and try to install, it is located here:

[http://packages.ubuntu.com/hardy/ted](http://packages.ubuntu.com/hardy/ted)

You will probably run into dependency problems,though.

---

### Post by moodle on 2009-07-09
Thanks Starcraft and Mtchy.

Starcraft,
Ted lacks many basic features, but that's exactly what I like about it.  I really enjoyed using Jarte on Windows, and I wanted something similar on Linux.  I've found Kate, which is brilliant, but unfortunately it lacks rich text editing.  Thanks for pointing me to AbiWord.  I like Abiword, but (this may sound strange) it does too much for me.

Michy,
You're right, there are dependency issues, so the .deb refused to install. Thanks for directing me to that page.

---

### Post by gumbygum on 2009-07-13
I would also like to install Ted, because I'm looking for an alternative to Open Office, which frequently seems to crash on my system, and AbiWord, which takes forever to open RTF files for some unknown reason. (I save all my files as RTF)

I found this page of Ted downloads:
[ftp://ftp.nluug.nl/pub/editors/ted](ftp://ftp.nluug.nl/pub/editors/ted)

Can any of these files be easily installed on my system? I'm running Linux Mint Gloria.

I also liked Jarte on Windows, and wish there was a similar program for Linux.

---

### Post by moodle on 2009-07-13
> **gumbygum said:**
> 

I found this page of Ted downloads:
[ftp://ftp.nluug.nl/pub/editors/ted](ftp://ftp.nluug.nl/pub/editors/ted)



Thanks for the link.  I tried installing the GB .deb on Ubuntu 9.04, but I got a dependency error.

---

### Post by Warpnow on 2009-08-15
Sorry for resurrecting a dead thread, but the dependency needed is listed in the link given. Ted-common. Click on it and install it first, then ted, and it works.

But Ted's menu item isn't added. Either type ted in the command line or add a menu item using the menu editor.

---

### Post by moodle on 2009-09-06
Thanks Warpnow, you're a superstar!

---

### Post by gumbygum on 2009-09-13
> **Warpnow said:**
> Sorry for resurrecting a dead thread, but the dependency needed is listed in the link given. Ted-common. Click on it and install it first, then ted, and it works.

But Ted's menu item isn't added. Either type ted in the command line or add a menu item using the menu editor.

Hi Warpnow. I don't see a file called "Ted-common" on the link I gave, [ftp://ftp.nluug.nl/pub/editors/ted](ftp://ftp.nluug.nl/pub/editors/ted)

Is that the link you were referring to? Ted-common is not there.

I do find a "Ted-common" here: [http://packages.debian.org/etch/editors/ted-common](http://packages.debian.org/etch/editors/ted-common)

but it is version 2.17-1. The latest Ted appears to be 2.20.

Would it work? For that matter, how do you install a dependency? I'm still a newb.

---

### Post by newsoft on 2009-09-13
This package is not stable and has many errors...stay away from it

---

