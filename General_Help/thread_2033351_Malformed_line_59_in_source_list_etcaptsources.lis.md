---
title: "Malformed line 59 in source list /etc/apt/sources.list (dist parse)"
date: 2012-07-26
forum: General Help
---

### Post by toxakst on 2012-07-26
Hello, i have just installed Linux Ubuntu 12.04 couple of hours ago, and trying to play around with it, but when i tried to do:
sudo apt-get update , i get this error:

E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

I have no idea how to fix it. Any help will be appreciated 

i did: 
gksudo gedit /etc/apt/sources.list 

here is what i have:

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

---

### Post by claracc on 2012-07-26
I don't know if it can help but you have two repeated lines in:

[QUOTE]## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
[COLOR="Red"]deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner[/COLOR]
[COLOR="YellowGreen"]deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner[/COLOR]
[COLOR="Red"]deb [http://archive.canonical.com/](http://archive.canonical.com/) precis peartner[/COLOR]
[COLOR="YellowGreen"]deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner[/COLOR]
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main 


Remove the repeated ones.

---

### Post by toxakst on 2012-07-26
i didn't fix my problem, when i comment those two repeated lines, i get another problem:
E: Malformed line 60 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

so...don't know, any ideas ?
cuz i can't even open Ubuntu software Centre because of this

---

### Post by codemaniac on 2012-07-26
> **toxakst said:**
> i didn't fix my problem, when i comment those two repeated lines, i get another problem:
E: Malformed line 60 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

so...don't know, any ideas ?
cuz i can't even open Ubuntu software Centre because of this


You can recreate your sources.lst from the below link .

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by claracc on 2012-07-26
What lines have you commented?

If I click on the link: deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner, the browser answers not found this url, note, /precise is part of the link

But if I click on deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner , the browser goes to the required software packages, note that here precise is separate of the link and it is not part of it.

So I would comment the following lines:
deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner

I think you have messed your sources.list by deleting the blank space.

---

### Post by toxakst on 2012-07-26
Thanks a lot, buddy, it fixed the problem

---

### Post by claracc on 2012-07-26
Glad you got fixed your problem.

Please, mark the thread as solved with "thread tools" in the right upper part of the page, in this way, other people can find solutions easily.

---

