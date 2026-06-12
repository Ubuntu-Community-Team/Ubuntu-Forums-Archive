---
title: "apt-get update error"
date: 2012-07-31
forum: General Help
---

### Post by Ditchdoc7893 on 2012-07-31
Hello.

I just tried to run the command sudo apt-get update and got the following error back

E: Malformedline 60 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read

Anyone have any ideas on this?

Thanks!

---

### Post by Toz on 2012-07-31
There is an error on line 60 of your etc/apt/sources.list file. Feel free to post the contents back if you need some assistance with finding the error.

---

### Post by Ditchdoc7893 on 2012-07-31
The line in question is as follows:

deb [http://archive.canonical.com/](http://archive.canonical.com/) partner

---

### Post by Toz on 2012-07-31
Which version of ubuntu are you running? If 12.04, it should read:
```
deb http://archive.canonical.com/ubuntu precise partner
```

---

### Post by Ditchdoc7893 on 2012-07-31
I am running 12.04. That could be the problem. Let me insert that into the code and see if that works. Thanks for the assistance. I'll repost if successful or not.

---

### Post by Ditchdoc7893 on 2012-08-01
Looks like it still returns an error. From both terminal and update-manager it returns the following:

Check your Internet connection.

W:Failed to fetch [http://archive.canonical.com/dists/ubuntu/precise/source/Sources](http://archive.canonical.com/dists/ubuntu/precise/source/Sources)  404  Not Found [IP: 91.189.92.191 80]
, W:Failed to fetch [http://archive.canonical.com/dists/ubuntu/partner/source/Sources](http://archive.canonical.com/dists/ubuntu/partner/source/Sources)  404  Not Found [IP: 91.189.92.191 80]
, W:Failed to fetch [http://archive.canonical.com/dists/ubuntu/precise/binary-amd64/Packages](http://archive.canonical.com/dists/ubuntu/precise/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.191 80]
, W:Failed to fetch [http://archive.canonical.com/dists/ubuntu/partner/binary-amd64/Packages](http://archive.canonical.com/dists/ubuntu/partner/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.191 80]
, W:Failed to fetch [http://archive.canonical.com/dists/ubuntu/precise/binary-i386/Packages](http://archive.canonical.com/dists/ubuntu/precise/binary-i386/Packages)  404  Not Found [IP: 91.189.92.191 80]
, W:Failed to fetch [http://archive.canonical.com/dists/ubuntu/partner/binary-i386/Packages](http://archive.canonical.com/dists/ubuntu/partner/binary-i386/Packages)  404  Not Found [IP: 91.189.92.191 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

First, there is obviously no problem with the internet connection as I am sending this message from the same connection as the update manager is attached to. There is only one so there should be no mistake there. I'm pasting a copy of the sources.list file. If you wouldn't mind, take a look and see if if you can spot the error. Thanks!

---

### Post by Toz on 2012-08-01
For the record, here is your /etc/apt/sources.list file:
```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/ 

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/ 
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted 

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to 
# newer versions of the distribution. 
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted 

## Major bug fix updates produced after the final release of the 
## distribution. 
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team. Also, please note that software in universe WILL NOT receive any 
## review or updates from the Ubuntu security team. 
deb http://us.archive.ubuntu.com/ubuntu/ precise universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe 
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse 

## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu precise-security main restricted 
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted 
deb http://security.ubuntu.com/ubuntu precise-security universe 
deb-src http://security.ubuntu.com/ubuntu precise-security universe 
deb http://security.ubuntu.com/ubuntu precise-security multiverse 
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse 

## Uncomment the following two lines to add software from Canonical's 
## 'partner' repository. 
## This software is not part of Ubuntu, but is offered by Canonical and the 
## respective vendors as a service to Ubuntu users. 
# deb http://archive.canonical.com/ubuntu precise partner 
# deb-src http://archive.canonical.com/ubuntu precise partner 

## This software is not part of Ubuntu, but is offered by third-party 
## developers who want to ship their latest software. 
deb http://extras.ubuntu.com/ubuntu precise main 
deb-src http://extras.ubuntu.com/ubuntu precise main 
deb http://archive.canonical.com/ ubuntu precise partner 
deb-src http://archive.canonical.com/ ubuntu precise partner
```

The last two lines are incorrect, there should be no space between the com/ and ubuntu.

---

### Post by Ditchdoc7893 on 2012-08-01
I'll give it a try. Thanks for your help again!

---

### Post by Ditchdoc7893 on 2012-08-01
Perfect! Thank you for your help Toz! Will mark solved!

---

