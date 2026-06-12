---
title: "installing libc6-dbg"
date: 2010-11-02
forum: General Help
---

### Post by lilipop on 2010-11-02
hi,
i have the latest ubuntu and i try to install the libc6-dbg, but when i do it there comes a windows sayng me waht u can see in the attached picture

so what i have to do to solve it??

i thank u in advance

---

### Post by matt_symes on 2010-11-02
Hi

Open a terminal and type

sudo apt-get install libc6-dbg

and enter your password.

Post the output of that command into a post here.

Be sure put the output between [code] tags

Kind regards

---

### Post by d5xtgr on 2010-11-02
I don't know if this is relevant to the problem, but I observe that the window style in that picture is not in fact of the most recent release of ubuntu; it appears to be of 10.04.  I hope this information is helpful.

---

### Post by lilipop on 2010-11-03
iura@silver-blade:~$ sudo apt-get install libc6-dbg
[sudo] password for iura: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
iura@silver-blade:~$ uname -a
Linux silver-blade 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686 GNU/Linux

---

### Post by matt_symes on 2010-11-03
Hi

> **lilipop said:**
> iura@silver-blade:~$ sudo apt-get install libc6-dbg
[sudo] password for iura: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
iura@silver-blade:~$ uname -a
Linux silver-blade 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686 GNU/Linux

Did you have synaptic package manager open when you ran that, or the software centre? If so close and repost as /var/lib/dpkg/ is locked. Something is locking it.

Kind regards

---

### Post by lilipop on 2010-11-09
iura@silver-blade:~$ sudo apt-get install libc6-dbg
[sudo] password for iura: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  sdparm
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libc6-dbg
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.5MB of archives.
After this operation, 55.9MB of additional disk space will be used.
Err [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) lucid-updates/main libc6-dbg 2.11.1-0ubuntu7.5
  Could not resolve 'pt.archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main libc6-dbg 2.11.1-0ubuntu7.5
  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-dbg_2.11.1-0ubuntu7.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-dbg_2.11.1-0ubuntu7.5_i386.deb)  Could not resolve 'security.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
iura@silver-blade:~$

mu linux version:: 10.04 LTS



and one more thing hapens when i try to update the system trught the update manager:::


W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://pt.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'pt.archive.ubuntu.com'

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'pt.archive.ubuntu.com'

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'pt.archive.ubuntu.com'

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2)  Could not resolve 'pt.archive.ubuntu.com'

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'pt.archive.ubuntu.com'

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Could not resolve 'pt.archive.ubuntu.com'

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'pt.archive.ubuntu.com'

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'pt.archive.ubuntu.com'

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'pt.archive.ubuntu.com'

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'pt.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.



and i always have open the sunapic or the update manager at once.

---

