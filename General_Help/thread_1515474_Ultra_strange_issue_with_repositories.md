---
title: "Ultra strange issue with repositories"
date: 2010-06-22
forum: General Help
---

### Post by Carlo1973 on 2010-06-22
I'm having an ultra strange issue right now with the repositories.

A few days ago I updated ubuntu 10.04 x64 on my laptop. Everything  was working great, no issues. Then I had to fly out to Calgary on business. The hotel's wireless was acting really funky while I was trying to download and install skype. Next thing I know I'm getting messages stating I've got dual listings for repositories, and a bunch of other stuff like invalid keys. I took a look at my repository list, and it appears that all my repositories got messed up. It wasn't much, there was the default repositories and I had also included Medibuntu and the Java repositories. Those both disappeared. In their place were the default repository for Ubuntu - 3 times. Not sure what was going on, I deleted the ones I thought were the messed up ones. Now I'm getting errors stating that my repository list is corrupt, and more errors regarding the keys. My only thinking is that while it was trying to update itself with the horrible connection that the list file didn't close properly and got buggered.

I don't think I need to reinstall fresh just to fix the repository lists. But as it stands right now I can't update or install any software. Can someone give me a hand on fixing these? I'm thinking that due the corrupt list, I'm going to have to purge out the keys and the current list and re-input the information.

Assistance would be greatly appreciated!

Thanks!

Carlo

---

### Post by bodhi.zazen on 2010-06-22
Post the contents of

/etc/apt/sources.list

More likely then not it is a simple syntax error that is easily fixed.

---

### Post by Carlo1973 on 2010-06-24
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid

---

### Post by tgm4883 on 2010-06-24
What is the output of 

```
ls -l /etc/apt/sources.list.d/
```

and 

```
apt-get update
```

---

### Post by Carlo1973 on 2010-06-24
Through some manipulation and guessing I've gotten it to stop giving errors. However I'm not sure 100% if I've restored the default Repositories. I ended up trying to pick and choose the keys and the repositories that were getting the error messages and remove them. This included the CD repository and keys. I've since managed to get the partner repositories working, but I could have sworn there were more than 2 repositories listed within Software Sources under the Other Software tab.

When I was first fighting with it sudo apt-get update -f would give errors related to the pgp keys.

---

### Post by tgm4883 on 2010-06-24
The list you posted looks correct. The repos on the end are actually different than the ones in the beginning of the file.

---

