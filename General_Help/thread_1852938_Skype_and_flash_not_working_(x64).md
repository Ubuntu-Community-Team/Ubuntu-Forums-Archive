---
title: "Skype and flash not working (x64)"
date: 2011-10-01
forum: General Help
---

### Post by Kinetic_lord on 2011-10-01
Hello,

I have a 64bit Ubuntu installation on my computer.

Skype and Flash can not be installed, I keep getting complaints related to some 'ia32-libs'. 

I would like to know how I can get them to work and why in the world did the 'ia32-libs' package got removed from the repositories if it's used by two important applications.

Thank you.

---

### Post by philinux on 2011-10-01
> **Kinetic_lord said:**
> Hello,

I have a 64bit Ubuntu installation on my computer.

Skype and Flash can not be installed, I keep getting complaints related to some 'ia32-libs'. 

I would like to know how I can get them to work and why in the world did the 'ia32-libs' package got removed from the repositories if it's used by two important applications.

Thank you.

Ok. Let's have a look at your sources.

cat /etc/apt/sources.list

And can you post the error message you got.

---

### Post by Kinetic_lord on 2011-10-01
deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted multiverse universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

There you go.

---

### Post by Kinetic_lord on 2011-10-01
When I try to install either of them it says that dependency is not satisfiable: ia32-libs.

As far as I googled I found out that they were removed due to bugs, but I need to get these two apps running and I can barely find solutions that work.

---

### Post by philinux on 2011-10-01
Go to.

System Admin Software sources. Un tick the cdrom and make sure the other 4 are ticked. Then retry.

---

### Post by Kinetic_lord on 2011-10-01
I did not mention that the distribution is running off a memory stick, should I still follow the instructions in the last post?

---

### Post by Kinetic_lord on 2011-10-01
Bump

---

### Post by Kinetic_lord on 2011-10-02
[http://ubuntuguide.net/install-skype-on-ubuntu-11-04-natty-narwhal-3264-bit](http://ubuntuguide.net/install-skype-on-ubuntu-11-04-natty-narwhal-3264-bit)

---

### Post by ottosykora on 2011-10-02
for flash it helped me to install the flash aid to the firefox and then via this I was able to select from more then one flash version directly from adobe.

Skype is in the repositories and works fine, you just have to go the software center and enable the partner repository. All works from there without problems also on x64.

---

