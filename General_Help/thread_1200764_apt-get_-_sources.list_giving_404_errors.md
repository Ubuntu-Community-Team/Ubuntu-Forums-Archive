---
title: "apt-get - sources.list giving 404 errors"
date: 2009-06-30
forum: General Help
---

### Post by monteros on 2009-06-30
Hey folks, I am having a problem with a *2.6.20-17-generic #2 SMP Wed Aug 20 16:47:34 UTC 2008 i686 GNU/Linux* box.

I am trying to run sudo apt-get update and or install apps, and I am  getting things like this:

> Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe debsums 2.0.30
  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/d/debsums/debsums_2.0.30_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/d/debsums/debsums_2.0.30_all.deb)  404 Not Found [IP: 91.189.88.40 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


I can't seem to resolve it, and it would seem that all I need to do is update the /etc/apt/sources.list file and run with it, but I can't seem to locate a valid list of current sources.  Chalk it up to being less savvy than I should -=/

Here are the contents of my /etc/apt/sources.list

> /etc$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse


Anyone have time to offer some advice?

Thanks in advance,
-monteros

---

### Post by NilsE on 2009-06-30
I think the answer may be that Feisty is no longer supported or the repos are closed.

Take a look at the link in your sources.list on how to upgrade to a newer release

---

### Post by michy99 on 2009-06-30
Feisty is no longer supported. The repositories have been moved to```
http://old-releases.ubuntu.com/
```You can change your sources.list to the new location, but the best thing is to update to 8.04 or 9.04.

---

### Post by monteros on 2009-06-30
> **michy99 said:**
> Feisty is no longer supported. The repositories have been moved to```
http://old-releases.ubuntu.com/
```You can change your sources.list to the new location, but the best thing is to update to 8.04 or 9.04.

Thanks guys, will do.

---

### Post by audience of one on 2009-07-08
> **michy99 said:**
> Feisty is no longer supported. The repositories have been moved to```
http://old-releases.ubuntu.com/
```You can change your sources.list to the new location, but the best thing is to update to 8.04 or 9.04.

How do I edit the sources.list?  I added an incorrect line in adept, and now it won't open. The file is read only and won't let me chmod it.

---

### Post by fooman on 2009-07-08
> **audience of one said:**
> How do I edit the sources.list?  I added an incorrect line in adept, and now it won't open. The file is read only and won't let me chmod it.

did you try:

```
gksudo gedit /ect/apt/sources.list
```

yeah,  1000 posts!!  :p

---

### Post by michy99 on 2009-07-08
You need to edit it as root. In a terminal, enter```
gksudo gedit /etc/apt/sources.list
```

---

### Post by audience of one on 2009-07-08
> **fooman said:**
> did you try:

```
gksudo gedit /ect/apt/sources.list
```

yeah,  1000 posts!!  :p

so I must have done something wrong. I put that in my console, it asked me for the password, but then went back to the command line.  Also, I am on 9.04.

---

### Post by audience of one on 2009-07-08
> **audience of one said:**
> so I must have done something wrong. I put that in my console, it asked me for the password, but then went back to the command line.  Also, I am on 9.04.
I got, it thanks, I did a sudo vi and the file and removed the bad line, and adept now comes up.  Thanks for your help.

---

