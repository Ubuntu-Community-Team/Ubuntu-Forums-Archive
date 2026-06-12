---
title: "update manager: cannot initialize the package information"
date: 2010-11-19
forum: General Help
---

### Post by noelraxit1 on 2010-11-19
hi guys help required

i am unable to open update manager 
when i open it , it gives back a msg stating that cannot initialize the package information.

and here is the error msg. 

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

And when i tried with #sudo apt-get update

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

and even i tried with deleting that file(security.ubuntu.com_ubuntu_dists_maverick-security_restricted_binary-i386_Packages) but was unsuccessful.

guys please Help me.....!

Thanks 
Regards
Noel

---

### Post by Hippytaff on 2010-11-19
What does your sources list look like
```

cat /var/apt/sources.list

```

---

### Post by plucky on 2010-11-19
> **Hippytaff said:**
> What does your sources list look like
```

cat /var/apt/sources.list

```

That would be ```
cat /etc/apt/sources.list
```

---

### Post by Hippytaff on 2010-11-19
> **plucky said:**
> That would be ```
cat /etc/apt/sources.list
```
 
oops - I'm having a bad day :-s
 
Thanks for correcting it :-)

---

### Post by noelraxit1 on 2010-11-19
this is what it shows when i type

#cat /etc/apt/sources.list


# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse

Regards
Noel

---

### Post by Hippytaff on 2010-11-19
Can't see anything wrong with that
 
try
```

gdsudo gedit /etc/apt/sources.list

```
 and edit these lines by putting a hash in front```

# deb [[COLOR=#444444]http://security.ubuntu.com/ubuntu[/COLOR]]("http://security.ubuntu.com/ubuntu") maverick-security main restricted
# deb-src [[COLOR=#444444]http://security.ubuntu.com/ubuntu[/COLOR]]("http://security.ubuntu.com/ubuntu") maverick-security main restricted
# deb [[COLOR=#444444]http://security.ubuntu.com/ubuntu[/COLOR]]("http://security.ubuntu.com/ubuntu") maverick-security universe
# deb-src [[COLOR=#444444]http://security.ubuntu.com/ubuntu[/COLOR]]("http://security.ubuntu.com/ubuntu") maverick-security universe
# deb [[COLOR=#444444]http://security.ubuntu.com/ubuntu[/COLOR]]("http://security.ubuntu.com/ubuntu") maverick-security multiverse
# deb-src [[COLOR=#444444]http://security.ubuntu.com/ubuntu[/COLOR]]("http://security.ubuntu.com/ubuntu") maverick-security multiverse

```
 
Save it and do sudo apt-get upgrade - are there still errors (Remember to undo this after)

---

### Post by noelraxit1 on 2010-11-19
is it  gksudo

---

### Post by noelraxit1 on 2010-11-19
thank you Hippytaff

its working i'm very glad for your help....

---

### Post by Hippytaff on 2010-11-19
This is just a workaround though - the # mean that the security updates won't happen. This was just to test whether there was something about these lines that was causing the problem...I wouldn't leave your sources.list file like this :-)
 
Unless of course sudo ap-get update && sudo apt-get upgrade fixed the problem, and you removed the hashes-# and it wokrs ok now.
 
Let me know :-)

---

### Post by noelraxit1 on 2010-11-21
dude i got the same problem again.... and now i tried removing hashes.....

---

### Post by plucky on 2010-11-23
> **noelraxit1 said:**
> dude i got the same problem again.... and now i tried removing hashes.....

The previous suggestion removed the sources which is the reason it worked.
Add back the sources and try the suggestion below

To fix the problem you have to delete the file that is causing the problem.

Open a terminal and copy and paste each of these commands in turn ```
cd /var/lib/apt/lists/
sudo rm security.ubuntu.com_ubuntu_dists_maverick-security_restricted_binary-i386_Packages
sudo apt-get update
```

and see if it now works.

Post any errors.

Good Luck

---

