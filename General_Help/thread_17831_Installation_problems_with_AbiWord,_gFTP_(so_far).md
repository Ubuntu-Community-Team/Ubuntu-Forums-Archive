---
title: "Installation problems with AbiWord, gFTP (so far)"
date: 2005-03-03
forum: General Help
---

### Post by leaded on 2005-03-03
I've been going through the Ubuntu guide and ubuntuguide.org and have run into a snag. I added the extra repositories, as mentioned in almost every step. First, after a fresh install, and the extra repos, I did an apt-get update and apt-get upgrade. Since then, I've only installed the Flash plugin, numlockx, gnome-clipboard-daemon, and Acroread (and it's plugin).

On Fedora I've been using AbiWord so I tried to install it here in Ubuntu. Here's the error that I get.
```
$ sudo apt-get install abiword
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  abiword: Depends: libenchant1 but it is not installable
E: Broken packages

```

I get the same error when trying to install abiword-gnome. I've also tried it in Synaptic but gotten the same errors. I had an Ubuntu installation a few months ago (accidently deleted it, oops) and it seemed like this is the method I had installed AbiWord then, and it worked fine. 

What do I need to do to get AbiWord installed? I've been using Linux exclusively for almost a year now, using the command line all the time, so I can handle any type of instruction without having to worry about newbie-ness  :wink: 

Thanks in advance!

EDIT: I forgot to mention, that I decided to go through the rest of the guide and ran into this problem for gFTP...
```
$ sudo apt-get install gftp
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gftp: Depends: gftp-gtk (= 2.0.17-6) but it is not going to be installed
        Depends: gftp-text (= 2.0.17-6) but it is not going to be installed
E: Broken packages
```

Any help would be much appreciated!

---

### Post by leaded on 2005-03-04
No one? 

I did a fresh install yesterday on another hard drive and came up with the same results  ](*,)

---

### Post by kassetra on 2005-03-04
[QUOTE=leaded]No one? 

I did a fresh install yesterday on another hard drive and came up with the same results  ](*,)[/QUOTE]

Let me see your sources.list file... sounds like something may be borked there.

---

### Post by az on 2005-03-04
Yeah, since abiword is on your cd.

---

### Post by factotum218 on 2005-03-05
I had the same probelm trying to install gftp. I have the apt/sources.list modified to match with the unofficial how-to and have done a few apt-get upgrades since then.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

<br>

Here is the dep error for gftp:

The following packages have unmet dependencies:
  gftp: Depends: gftp-gtk (= 2.0.17-6) but 2.0.17-6ubuntu0.2 is to be installed
        Depends: gftp-text (= 2.0.17-6) but it is not going to be installed
E: Broken packages

---

### Post by factotum218 on 2005-03-06
bump

---

### Post by johnwlittle on 2005-03-07
I have the same source.list and the same gFTP error.

---

