---
title: "Update Error Message"
date: 2006-06-15
forum: General Help
---

### Post by jeisma on 2006-06-15
hi!

how do you fix an error like this?

> 
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages [585kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [88.5kB]
67% [6 Packages gzip 0] [5 Packages 327246/585kB 55%]
gzip: stdin: not in gzip format
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  Sub-process gzip returned an error code (1)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages


this is my sources file.

> 
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse



thanks!

---

### Post by inspired on 2006-06-20
I to would like to know how to sort this issue out.
I am trying to upgrade breezy 5.10 to Dapper 6.06

I have updated my sources list as per instructions given [here]("https://help.ubuntu.com/community/DapperUpgrades")
I have then issued the command :
sudo apt-get update && sudo apt-get dist-upgrade 

as per instructions on that same page.
But I get the following result:

> 
... snip ...
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages [95.2kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources [975kB]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources [46.6kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [37.7kB]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [22.1kB]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [14B]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [14B]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources [14B]
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources [14B]
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources [14B]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages [121kB]
97% [37 Packages gzip 0] [Connecting to archive.ubuntu.com (85.133.25.7)]                                   20.1kB/s 7s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  Sub-process gzip returned an error code (1)
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources [57.5kB]
97% [Working]                                                                                               20.1kB/s 7s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
  Sub-process gzip returned an error code (1)
Fetched 4706kB in 3m3s (25.6kB/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  Sub-process gzip retur ned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz)  Sub-process gzip returned an  error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

I am still looking for some info on what this error is about.
Any help would be greatly appreciated.

Thanks,

Jonathan

---

### Post by jeisma on 2006-06-20
hi!

unfortunately, we are both having the same problems.

i am also trying to upgrade breezy install.

too bad for us having this problem...

---

### Post by inspired on 2006-06-20
jeisma --
Try the suggestion made [here]("http://ubuntuforums.org/showthread.php?p=1115981") regarding changing all refs for http:// over to ftp:// in yours sources.list file.
It worked for me.

---

### Post by jeisma on 2006-06-20
hi!

i based my sources.list [here]("http://www.psychocats.net/ubuntu/sources")

how about you?

i will try to run update using ftp instead.

thanks.

---

### Post by arphe_el on 2006-06-21
i'm having an error upgrading my system from hoary to breezy here are the following error after i ran the cd install and processed it:

errors where encountered while processing
postfix
lsb-core
lsb-graphics
lsb-cxx
lsb
mailx
mutt

any solutions that be of great help! thank you and GODspeed!

---

