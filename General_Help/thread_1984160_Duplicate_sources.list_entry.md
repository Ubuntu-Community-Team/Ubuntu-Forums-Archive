---
title: "Duplicate sources.list entry"
date: 2012-05-21
forum: General Help
---

### Post by neuman1812 on 2012-05-21
Ran the 
```
apt-get update
```

```
Fetched 19.5 MB in 16s (1,199 kB/s)                                                                                                                                                 
Reading package lists... Done
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ precise/multiverse amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ precise/restricted i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ precise/main i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ precise/multiverse i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ precise/universe i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

Ran it again and it did not fix the entries.
So I tried
```

$ grep -v ^# /etc/apt/sources.list | sort | uniq -c | sort
     17 
      1 deb http://extras.ubuntu.com/ubuntu precise main
      1 deb http://security.ubuntu.com/ubuntu precise-security main restricted
      1 deb http://security.ubuntu.com/ubuntu precise-security multiverse
      1 deb http://security.ubuntu.com/ubuntu precise-security universe
      1 deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
      1 deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
      1 deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
      1 deb http://us.archive.ubuntu.com/ubuntu/ precise-proposed restricted main multiverse universe
      1 deb http://us.archive.ubuntu.com/ubuntu/ precise restricted main multiverse universe
      1 deb http://us.archive.ubuntu.com/ubuntu/ precise universe
      1 deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
      1 deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
      1 deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
      1 deb-src http://extras.ubuntu.com/ubuntu precise main
      1 deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
      1 deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
      1 deb-src http://security.ubuntu.com/ubuntu precise-security universe
      1 deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
      1 deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted
      1 deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
      1 deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
      1 deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
      1 deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
      1 deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
```


And I dont see the duplicate entries....   Any help?

Here's my Sources.list
```
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

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse



# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

```

---

### Post by Azdour on 2012-05-21
Hi

Sources can also be found in:

```
/etc/apt/sources.list.d
```

This may be where the duplicates are and they may be spread over more than one file.

---

### Post by neuman1812 on 2012-05-21
> **Azdour said:**
> Hi

Sources can also be found in:

```
/etc/apt/sources.list.d
```

This may be where the duplicates are and they may be spread over more than one file.

I got nothing in that directory even with view hidden files turned on

---

### Post by Azdour on 2012-05-21
Hi,

Ok, I'm not an expert with sources.list, could the following be your problem

These lines:
```

1 deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
1 deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse

```
In the line below they are repeated because you are asking for restricted, main and multiverse which you already have in the lines above:
```

1 deb http://us.archive.ubuntu.com/ubuntu/ precise restricted main multiverse universe

```

And this is a repeat of part of the line above
```

1 deb http://us.archive.ubuntu.com/ubuntu/ precise universe

```

What happens if you comment out the following line?:
```
deb http://us.archive.ubuntu.com/ubuntu/ precise restricted main multiverse universe
```

From what I gather the lines in the sources.list are defined like this:
```

deb uri distribution [component1] [component2] [...]

```

In your sources.list you are repeating the same components on several lines; main, restricted, multiverse and universe

---

