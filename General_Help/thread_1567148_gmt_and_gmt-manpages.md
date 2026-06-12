---
title: "gmt and gmt-manpages"
date: 2010-09-03
forum: General Help
---

### Post by rvsjimbo on 2010-09-03
Hello,

Don't know if others have had this problem, but I find that whichever order I try and install gmt and gmt-manpages, they don't seem to want to exist together on a machine. Can anyone tell me how to get around this please?

Thanks!

Paul
~~~~ (using Linux Mint 8 - which I believe is an Ubuntu variant)

---

### Post by QLee on 2010-09-03
[QUOTE=rvsjimbo]Hello,

Don't know if others have had this problem, but I find that whichever order I try and install gmt and gmt-manpages, they don't seem to want to exist together on a machine. Can anyone tell me how to get around this please?...
~~~~ (using Linux Mint 8 - which I believe is an Ubuntu variant)[/QUOTE]
Well, you are probably not going to be able to. The package gmt-manpages conflicts with package gmt (which replaces gmt-manpages), so the package manager is trying to prevent you from doing something which shouldn't be done, just like a package manager should do. At least, this is true for newer versions of Ubuntu, can't really say about Mint8.

---

### Post by rvsjimbo on 2010-09-03
Its definately a bug though. Its like saying, you can have the man page for the ls command installed, or the command itself, but not both... So, I think its an Ubuntu problem, and not specific to Mint. The /etc/apt/sources.list file looks like this (the bits that are not commented out):

deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) isadora main upstream import
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid partner
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free

TTFN,

Paul.

---

### Post by QLee on 2010-09-03
[QUOTE=rvsjimbo]Its definately a bug though. Its like saying, you can have the man page for the ls command installed, or the command itself, but not both... ...[/QUOTE]

No that's not what is being said, please reread what I wrote. 

And, by the way as a test, when you have gmt installed, what happens when you enter man gmt in a terminal?

---

### Post by rvsjimbo on 2010-09-03
Okay,

Thank you. Point taken :-) 

The gmt package appears to include the gmt manual pages... So I'm feeling a bit daft now. But I still would like to know why installing the gmt-manpages package, gets rid of the main gmt package... I would have thought the logical thing would be for it to say something like "the man pages are already installed" and leave it at that...

Anyway, you've solved my problem (which I suppose I didn't really have!), so thank you :-)

Have a great weekend,

Paul.

---

