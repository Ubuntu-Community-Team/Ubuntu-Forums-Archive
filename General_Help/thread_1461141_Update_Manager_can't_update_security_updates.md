---
title: "Update Manager can't update security updates"
date: 2010-04-23
forum: General Help
---

### Post by rva1945 on 2010-04-23
libnss3-1d
xulrunner-1.9.1
xulrunner-1.9.1-gnome support

After click on install updates and entering password, a message says "Some of the packages could not be retrieved from the server(s). Do you want to continue, ignoring these packages? Yes/No.

If I answer No, this message appears:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.6-0ubuntu0.9.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.6-0ubuntu0.9.10.1_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]

If Yes, it tries to download but immediately:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.6-0ubuntu0.9.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.6-0ubuntu0.9.10.1_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]

It has always installed the updates with no problems, until these 3 updates remain in pending installation status.

---

### Post by plucky on 2010-04-24
> **rva1945 said:**
> libnss3-1d
xulrunner-1.9.1
xulrunner-1.9.1-gnome support

After click on install updates and entering password, a message says "Some of the packages could not be retrieved from the server(s). Do you want to continue, ignoring these packages? Yes/No.

If I answer No, this message appears:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.6-0ubuntu0.9.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.6-0ubuntu0.9.10.1_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]

If Yes, it tries to download but immediately:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.6-0ubuntu0.9.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.6-0ubuntu0.9.10.1_i386.deb)
  404  Not Found [IP: 91.189.88.31 80]

It has always installed the updates with no problems, until these 3 updates remain in pending installation status.

Please post your sources.list

Open a terminal and ```
cat /etc/apt/sources.list
``` Then copy and paste the result to the forum.

Please paste between [noparse]```

```[/noparse] brackets.

Good Luck

---

### Post by rva1945 on 2010-04-24
> **plucky said:**
> Please post your sources.list

Open a terminal and ```
cat /etc/apt/sources.list
``` Then copy and paste the result to the forum.

Please paste between [noparse]```

```[/noparse] brackets.

Good Luck

I didn't find the code and /code strings:

robert@rvasystem:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
robert@rvasystem:~$

---

### Post by philinux on 2010-04-24
Try this.

Go into system>admin>software sources and change the server to say main.

---

### Post by rebelxt on 2010-04-27
This worked for me.  Thanks.

However, it makes me wonder what the consequences of the server choice are.  Will leaving the server set to Main result in other packages not being found?  Will one server typically have a faster download rate than the other?  Any other considerations?

---

