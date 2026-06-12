---
title: "Package Search question?"
date: 2012-06-29
forum: General Help
---

### Post by lhernandez on 2012-06-29
If I search for couchdb on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) I can see that version 1.0.1 is available. However, if I search from the command line with "apt-cache show couchdb" the version number seems to be different. Here's what I get.


Package: couchdb
Priority: optional
Section: universe/misc
Installed-Size: 84
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Erlang Packaging Team <pkg-erlang-devel@lists.alioth.debian.org>
Architecture: all
Version: 0.10.0-1ubuntu2
Replaces: couchdb-bin (<< 0.10.0~svn818859-0ubuntu1)
Depends: couchdb-bin (= 0.10.0-1ubuntu2)
Filename: pool/universe/c/couchdb/couchdb_0.10.0-1ubuntu2_all.deb

---

### Post by drmrgd on 2012-06-29
What happens if you run:

```
sudo apt-get update
```

and then run apt-cache?  I think the database might need updating.

---

### Post by lhernandez on 2012-06-29
I did try that before posting. Same result :(

---

### Post by Dave_L on 2012-06-29
You might not have the repositories enabled that contain version 1.0.1.

If you don't know how to determine that, please post your file "/etc/apt/sources.list".

---

### Post by drmrgd on 2012-06-29
> **Dave_L said:**
> You might not have the repositories enabled that contain version 1.0.1.

If you don't know how to determine that, please post your file "/etc/apt/sources.list".

Yeah, that was my next thought as well.  What version of Ubuntu are you running, and what does your sources list look like?  When I run the query with Kubuntu 12.04, I can see the updated package:


```
Package: couchdb
Priority: optional
Section: universe/misc
Installed-Size: 67
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Erlang Packaging Team <pkg-erlang-devel@lists.alioth.debian.org>
Architecture: all
Version: 1.0.1-0ubuntu18
Depends: couchdb-bin (>= 1.0.1-0ubuntu18)
Filename: pool/universe/c/couchdb/couchdb_1.0.1-0ubuntu18_all.deb
Size: 6910
MD5sum: 96eb1207aad533c6fba995e8d3db9d9b
SHA1: 6c9c71940f98474eb3e8d5f63cd3c4dd719d88e9
SHA256: 52b2225556d3c538d84857286cd4b78eb052b69e9a28b90a94b699497a89417e
Description-en: RESTful document oriented database, system DB
 Apache CouchDB is a distributed, fault-tolerant and schema-free
 document-oriented database accessible via a RESTful HTTP/JSON API. Among other
 features, it provides robust, incremental replication with bi-directional
 conflict detection and resolution, and is queryable and indexable using a
 table-oriented view engine with JavaScript acting as the default view
 definition language.
 .
 CouchDB is written in Erlang, but can be easily accessed from any environment
 that provides means to make HTTP requests. There are a multitude of third-party
 client libraries that make this even easier for a variety of programming
 languages and environments.
Homepage: http://couchdb.apache.org/
Description-md5: de4374e3ac909fb8393491cd86fb3a0b
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
```

---

### Post by lhernandez on 2012-06-29
I'm using Ubuntu 10.4 LTS. Here's my /etc/apt/sources.list

#
# deb cdrom:[Ubuntu-Server 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110719.2)]/ lucid main restricted

# deb cdrom:[Ubuntu-Server 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110719.2)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://packages.vmware.com/tools/esx/4.1latest/ubuntu](http://packages.vmware.com/tools/esx/4.1latest/ubuntu) lucid main restricted
deb [http://packages.vmware.com/tools/esx/4.1latest/ubuntu](http://packages.vmware.com/tools/esx/4.1latest/ubuntu) lucid main restricted

---

### Post by drmrgd on 2012-06-29
It looks like that's the most recent version of the package for 10.04.  Check out this link:

[http://packages.ubuntu.com/search?keywords=couchdb&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=couchdb&searchon=names&suite=lucid&section=all)

I think you were looking at the package list for Precise, which does indeed contain a more recent version.  

As 10.04 isn't supported any longer, and if you really need the updated package, I would recommend upgrading.

---

### Post by Dave_L on 2012-06-29
> **lhernandez said:**
> I'm using Ubuntu 10.4 LTS. Here's my /etc/apt/sources.list

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

You need to enable lucid-backports:

```
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
```

I'm also running Ubuntu 10.04, and version 1.0.1 of couchdb shows up for me in lucid-backports.

---

### Post by Cheesemill on 2012-06-29
> **drmrgd said:**
> As 10.04 isn't supported any longer, and if you really need the updated package, I would recommend upgrading.
10.04 is still supported for another year on desktops and another 3 years on servers.

---

### Post by drmrgd on 2012-06-29
> **Cheesemill said:**
> 10.04 is still supported for another year on desktops and another 3 years on servers.

Oh, sorry about that!  I misunderstood the support cycle, then.  Thought it was phased out as of 12.04 :redface:

In that case, enabling the backports is definitely the way to go!  Thanks for fixing my errors!

---

### Post by lhernandez on 2012-07-20
> **Dave_L said:**
> You need to enable lucid-backports:

```
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
```

I'm also running Ubuntu 10.04, and version 1.0.1 of couchdb shows up for me in lucid-backports.

This was my issue. Thanks You.

---

