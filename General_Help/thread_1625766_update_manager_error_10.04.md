---
title: "update manager error 10.04"
date: 2010-11-19
forum: General Help
---

### Post by MacKai on 2010-11-19
For a few weeks now my system has been giving me the following error(s)

at first I just thought it was a bad connection or overloaded server but it persists... how do I fix it? I want to up grade to Meercat but the instructions say to make all the updates first ...





W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/lucid/Release](http://linux.dropbox.com/ubuntu/dists/lucid/Release)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.88.46 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by sikander3786 on 2010-11-19
There are a few bad entries in your sources.list.

Please post the output of

```
cat /etc/apt/sources.list
```

---

### Post by MacKai on 2010-11-19
mackai@hogan:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid main restricted
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates main restricted
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid universe
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid universe
deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates universe
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid multiverse
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid multiverse
deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates multiverse
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-security main restricted
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-security main restricted
deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-security universe
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-security universe
deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-security multiverse
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-security multiverse
deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-backports restricted main multiverse universe
deb [http://ppa.launchpad.net/laurent-parenteau/full-circle-notifier/ubuntu](http://ppa.launchpad.net/laurent-parenteau/full-circle-notifier/ubuntu) lucid main
mackai@hogan:~$

---

### Post by sikander3786 on 2010-11-19
You don't need intrepid-backports repositories.

Edit sources.list by

```
gksudo gedit /etc/apt/sources.list
```

and comment this line with #

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

so that it looks like

> #deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

Save, close and update.

```
sudo apt-get update
```

---

### Post by sikander3786 on 2010-11-19
Sorry I missed one.

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

Add the signature following this.

```
sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E
```

Source:

[http://forums.dropbox.com/topic.php?id=25910](http://forums.dropbox.com/topic.php?id=25910)

Also see this if needed.

[https://www.dropbox.com/downloading?os=lnx](https://www.dropbox.com/downloading?os=lnx)

---

### Post by MacKai on 2010-11-19
O.K.  like this...


the error messages are gone... so I am getting all the updates i need then? 




# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid main restricted
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates main restricted
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid universe
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid universe
deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates universe
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid multiverse
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid multiverse
deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates multiverse
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-security main restricted
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-security main restricted
deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-security universe
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-security universe
deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-security multiverse
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-security multiverse
#deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-backports restricted main multiverse universe
deb [http://ppa.launchpad.net/laurent-parenteau/full-circle-notifier/ubuntu](http://ppa.launchpad.net/laurent-parenteau/full-circle-notifier/ubuntu) lucid main

---

### Post by sikander3786 on 2010-11-19
If there are no errors, apt-get is set up nicely.

For installing current updates,

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by MacKai on 2010-11-19
O.K. this is what I got on the second one...

 sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver pgp.mit.edu --recv-keys 5044912E
gpg: requesting key 5044912E from hkp server pgp.mit.edu
gpg: key 5044912E: "Dropbox Automatic Signing Key <linux@dropbox.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

---

### Post by sikander3786 on 2010-11-19
> **MacKai said:**
> O.K. this is what I got on the second one...

 sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver pgp.mit.edu --recv-keys 5044912E
gpg: requesting key 5044912E from hkp server pgp.mit.edu
gpg: key 5044912E: "Dropbox Automatic Signing Key <linux@dropbox.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
What is the output of apt-get update? If no errors, there are no more problems.

---

### Post by MacKai on 2010-11-19
> **sikander3786 said:**
> Sorry I missed one.



Add the signature following this.

```
sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E
```

Source:

[http://forums.dropbox.com/topic.php?id=25910](http://forums.dropbox.com/topic.php?id=25910)

Also see this if needed.

[https://www.dropbox.com/downloading?os=lnx](https://www.dropbox.com/downloading?os=lnx)




nope that was the results of this .. I haven't run "upgrade" yet just Update Manager .... how did it go bad ?

---

### Post by MacKai on 2010-11-19
Thanks for your help sikander3786



MacKai

---

### Post by sikander3786 on 2010-11-19
> **MacKai said:**
> nope that was the results of this .. I haven't run "upgrade" yet just Update Manager .... how did it go bad ?
Yes I know it was the output of apt-key adv command. And the output seems successful as it tells that the gpg key was already present.

If apt-get update or any other apt-get operation doesn't return any error, everything we did was successful.

Good Luck!

---

