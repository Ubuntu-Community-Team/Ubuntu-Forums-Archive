---
title: "Duplicate Support Warning"
date: 2009-06-29
forum: General Help
---

### Post by larry on 2009-06-29
Dear All,
When I try to update my system (sudo apt-get update) I usually get these warnings

Fetched 398kB in 3s (102kB/s)
Reading package lists... Done
W: GPG error: [http://cran.ch.r-project.org](http://cran.ch.r-project.org) jaunty/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D67FC6EAE2A11821
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems

I know where the first warning comes from (a repository for R statistical language), but I am unsure about the other one (which disappears if I issue the sudo apt-get command again).
Here is my /etc/apt/source_list file

~$ more /etc/apt/sources.list

##JAUNTY SUPPORTED
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty main restricted

##JAUNTY SUPPORTED - UPDATES
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

##JAUNTY SUPPORTED - PROPOSED
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty-proposed main restricted
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty-proposed main restricted

##JAUNTY SUPPORTED - SECURITY
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security main restricted

##JAUNTY COMMUNITY SUPPORTED
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty universe multiverse
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty universe multiverse

##JAUNTY COMMUNITY SUPPORTED - SECURITY
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security universe multiverse


##JAUNTY COMMUNITY SUPPORTED - UPDATES
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty-updates universe multiverse
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty-updates universe multiverse

##JAUNTY COMMUNITY SUPPORTED - PROPOSED
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty-proposed universe multiverse
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty-proposed universe multiverse

##JAUNTY BACKPORTS
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

##MEDIBUNTU
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

##CANONICAL
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) jaunty partner



#igraph library
deb [http://cneurocvs.rmki.kfki.hu](http://cneurocvs.rmki.kfki.hu) /packages/binary/
deb-src [http://cneurocvs.rmki.kfki.hu](http://cneurocvs.rmki.kfki.hu) /packages/source/

#to be able to have the latest R version
#deb http://<my.favorite.cran.mirror>/bin/linux/ubuntu jaunty/
deb [http://cran.ch.r-project.org/bin/linux/ubuntu](http://cran.ch.r-project.org/bin/linux/ubuntu) jaunty/

Apart from the last two repositories, which I use for rather specialized needs, can you spot anything wrong there?
Many thanks

larry

---

### Post by plucky on 2009-06-29
> W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-amd64_Packages)

Do you have a medibuntu.list file? Open a terminal and input
```
cat /etc/apt/sources.list.d/medibuntu.list
```

this is probably your duplicate source.

Either edit the one in your "sources.list" and put a # in front of it or delete the "medibuntu.list file in /etc/apt/sources.list.d/ directory. 


> W: GPG error: [http://cran.ch.r-project.org](http://cran.ch.r-project.org) jaunty/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D67FC6EAE2A11821


This is what the actual website says about adding the key ```
SECURE APT

The Ubuntu archives on CRAN are signed with the key of "Vincent Goulet <vincent.goulet@act.ulaval.ca>" with key ID E2A11821. You can fetch this key with

   gpg --keyserver subkeys.pgp.net --recv-key E2A11821

and then feed it to apt-key with

   gpg -a --export E2A11821 | sudo apt-key add -

Some people have reported difficulties using this approach. The issue was usually related to a firewall blocking port 11371. An alternative approach is to search for the key at http://keyserver.ubuntu.com:11371/ and copy the key to a plain text file, say key.txt. Then, feed the key to apt-key with

   sudo apt-key add key.txt

```

Good Luck

---

