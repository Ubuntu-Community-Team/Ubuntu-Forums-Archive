---
title: "Update Software Source List Error!!"
date: 2010-09-15
forum: General Help
---

### Post by Ahmad Rady on 2010-09-15
[SIZE=4][FONT=Georgia]Hi All;
I have problem with ( Software Source List Update )
This Pictures for my configuration
and error what I am talking about;

1- Main Ubuntu Software

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169553&stc=1&d=1284572568[/IMG]

2- Other Software

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169554&stc=1&d=1284572568[/IMG]

3- Updates

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169555&stc=1&d=1284572568[/IMG]

4- Authentication

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169556&stc=1&d=1284572568[/IMG]

5- Statistics

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169557&stc=1&d=1284572568[/IMG]

6- This The Update Manger When I press check

[IMG]http://i684.photobucket.com/albums/vv204/AhmadRady/9-2010/Screenshot-UpdateManager.png[/IMG]

7- This Error Appear

[IMG]http://i684.photobucket.com/albums/vv204/AhmadRady/9-2010/Screenshot-UntitledWindow.png[/IMG]

8- Text for the error

[/FONT][/SIZE]>  Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.bz2)  Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead. [SIZE=4][FONT=Georgia]So what is the reason?
What is solution?
What is the best configuration to get latest updates and software?


[/FONT][/SIZE]

---

### Post by philinux on 2010-09-15
Please post your sources list.

Open a terminal Applications>Accessories>Terminal

```
cat /etc/apt/sources.list
```

Post back here with list.

---

### Post by arrange on 2010-09-15
This may help you:
[http://ubuntuforums.org/showpost.php?p=4952791&postcount=10](http://ubuntuforums.org/showpost.php?p=4952791&postcount=10)

---

### Post by Ahmad Rady on 2010-09-15
> **philinux said:**
> Please post your sources list.

Open a terminal Applications>Accessories>Terminal

```
cat /etc/apt/sources.list
```Post back here with list.


This is

>   digiwise@DIGIWISE-PC:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted

# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security multiverse
digiwise@DIGIWISE-PC:~$ 
  

---

### Post by Ahmad Rady on 2010-09-15
> **arrange said:**
> This may help you:
[http://ubuntuforums.org/showpost.php?p=4952791&postcount=10](http://ubuntuforums.org/showpost.php?p=4952791&postcount=10)


I tried the two ways [-X

---

### Post by arrange on 2010-09-15
> **Ahmad Rady said:**
> I tried the two ways [-X
And...?

Can you also post (to check the hashes)```
cd /tmp
wget http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release
wget http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.bz2
md5sum Sources.bz2
grep multiverse/source/Sources.bz2 Release
```

---

