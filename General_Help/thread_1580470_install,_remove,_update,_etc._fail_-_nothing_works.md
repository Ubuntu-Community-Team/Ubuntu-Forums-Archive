---
title: "install, remove, update, etc. fail - nothing works!"
date: 2010-09-23
forum: General Help
---

### Post by ansariemail on 2010-09-23
I am unable to update any package due to the following error:

dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

complete error message:

```
Preconfiguring packages ...
(Reading database ... 318647 files and directories currently installed.)
Preparing to replace acroread 9.3.3-1lucid1 (using .../acroread_9.3.4-1lucid1_amd64.deb) ...
Unpacking replacement acroread ...
dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
A package failed to install. Trying to recover:
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
```If I try to remove acroread, here's what I get:

```
$ sudo dpkg configure -a
$ sudo apt-get remove acroread

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
libparted0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
acroread
0 upgraded, 0 newly installed, 1 to remove and 54 not upgraded.
1 not fully installed or removed.
After this operation, 152MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing acroread (--remove):
Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.
Errors were encountered while processing:
acroread
E: Sub-process /usr/bin/dpkg returned an error code (1)

```autoremove also does not work:

```
$ sudo apt-get autoremove

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  acroread
Suggested packages:
  libldap2
The following packages will be upgraded:
  acroread
1 upgraded, 0 newly installed, 0 to remove and 95 not upgraded.
1 not fully installed or removed.
Need to get 63.4MB of archives.
After this operation, 4,096B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.canonical.com/ubuntu/ lucid/partner acroread 9.3.4-1lucid1 [63.4MB]
Fetched 63.4MB in 2min 53s (365kB/s)                                                                                                           
Preconfiguring packages ...
(Reading database ... 318643 files and directories currently installed.)
Preparing to replace acroread 9.3.3-1lucid1 (using .../acroread_9.3.4-1lucid1_amd64.deb) ...
Unpacking replacement acroread ...
dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg exited unexpectedly


```install does not work:

```
$ sudo apt-get install acroread

Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
libldap2
The following packages will be upgraded:
acroread
1 upgraded, 0 newly installed, 0 to remove and 54 not upgraded.
1 not fully installed or removed.
Need to get 0B/63.4MB of archives.
After this operation, 4,096B of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package acroread.
(Reading database ... 318643 files and directories currently installed.)
Preparing to replace acroread 9.3.3-1lucid1 (using .../acroread_9.3.4-1lucid1_amd64.deb) ...
Unpacking replacement acroread ...
dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

``````
$sudo apt-get install acroread --reinstall

Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
libldap2
The following packages will be upgraded:
acroread
1 upgraded, 0 newly installed, 0 to remove and 54 not upgraded.
1 not fully installed or removed.
Need to get 63.4MB of archives.
After this operation, 4,096B of additional disk space will be used.
Get:1 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner acroread 9.3.4-1lucid1 [63.4MB]
Fetched 63.4MB in 2min 30s (420kB/s)
Preconfiguring packages ...
(Reading database ... 318643 files and directories currently installed.)
Preparing to replace acroread 9.3.3-1lucid1 (using .../acroread_9.3.4-1lucid1_amd64.deb) ...
Unpacking replacement acroread ...
dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

``````
$ sudo aptitude reinstall acroread

Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
The following packages will be REINSTALLED:
acroread
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 54 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the acroread package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the acroread package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download


```I am willing to edit configuration files if someone tells me what files and what changes I need to make.

Thanks.
P.S. I have ubuntu 10.4 lts 64 bit on lenovo t61p.

---

### Post by oldos2er on 2010-09-23
Try ```
sudo apt-get clean && sudo apt-get update && sudo apt-get install acroread
```

---

### Post by sikander3786 on 2010-09-23
In addition to oldos2er's suggestions, try

```

sudo apt-get install -f

```

and

```

sudo dpkg --configure -a

```

Also in Synaptic > Custom Filters > Broken and try to fix broken packages.

You've also got duplicate entries in sources.list. Post the output of

```

cat /etc/apt/sources.list

```

[COLOR="Red"]**EDIT:**[/COLOR] Please use the # code tags around the output from terminal from the top menu.

---

### Post by ansariemail on 2010-09-23
Tried all suggested options - output is given below.

```
$ sudo apt-get clean && sudo apt-get update && sudo apt-get install acroread

Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  libldap2
The following packages will be upgraded:
  acroread
1 upgraded, 0 newly installed, 0 to remove and 95 not upgraded.
1 not fully installed or removed.
Need to get 63.4MB of archives.
After this operation, 4,096B of additional disk space will be used.
Get:1 http://archive.canonical.com/ubuntu/ lucid/partner acroread 9.3.4-1lucid1 [63.4MB]
Fetched 63.4MB in 2min 14s (471kB/s)                                                                                       
Preconfiguring packages ...
(Reading database ... 318643 files and directories currently installed.)
Preparing to replace acroread 9.3.3-1lucid1 (using .../acroread_9.3.4-1lucid1_amd64.deb) ...
Unpacking replacement acroread ...
dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
``````
$ sudo dpkg --configure -a
$ sudo apt-get install -f

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  acroread
Suggested packages:
  libldap2
The following packages will be upgraded:
  acroread
1 upgraded, 0 newly installed, 0 to remove and 95 not upgraded.
1 not fully installed or removed.
Need to get 0B/63.4MB of archives.
After this operation, 4,096B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 318643 files and directories currently installed.)
Preparing to replace acroread 9.3.3-1lucid1 (using .../acroread_9.3.4-1lucid1_amd64.deb) ...
Unpacking replacement acroread ...
dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

``````
$ sudo dpkg --configure -a
$ cat /etc/apt/sources.list

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu lucid universe
deb-src http://archive.ubuntu.com/ubuntu lucid universe
deb http://archive.ubuntu.com/ubuntu lucid-updates universe
deb-src http://archive.ubuntu.com/ubuntu lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu lucid multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid multiverse
deb http://archive.ubuntu.com/ubuntu lucid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb http://archive.ubuntu.com/ubuntu lucid-security universe
deb-src http://archive.ubuntu.com/ubuntu lucid-security universe
deb http://archive.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-security multiverse
deb http://archive.ubuntu.com/ubuntu lucid-proposed restricted main multiverse universe

deb http://download.virtualbox.org/virtualbox/debian lucid non-free

```

---

### Post by sikander3786 on 2010-09-23
I think your apt cache has got corrupted. Time for some clean up. Follow with caution, keep a close eye and your mind on what you are doing and double check before deleting any files/text as advised.

Type
```

gksu nautilus /var/lib/dpkg/info

```

Find acroread, any files relating to it and rename them, delete them or move them to some other location whatever you prefer.

Now make a backup of your dpkg status file as you are going to edit it and might need to revert back to the original in case.

```

sudo cp /var/lib/dpgk/status /var/lib/dpkg/status.bak

```

Now edit the file

```

gksu gedit /var/lib/dpkg/status

```

Search for acroread and delete any lines relating to it. There might be more than one so go keep on searching until the end of the file.

Now type

```

sudo apt-get update

```

And tell me that the error message is gone. :-)


[COLOR="Red"]**EDIT:**[/COLOR] **You are doing everything as root, the system might not ask you to double check or even single check if deleting something. Be cautious or you might mess up your system.**

---

### Post by ansariemail on 2010-09-23
I removed the entire "Package: acroread" stanza and one more line down under Conffiles: related to acroread. It solved the problem!

I really appreciate your quick replies and help.

Thanks,
Nadeem

---

