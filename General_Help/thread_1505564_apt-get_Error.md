---
title: "apt-get Error"
date: 2010-06-09
forum: General Help
---

### Post by negatifo on 2010-06-09
I'm getting this error:
Reading package lists... Error!
E: Problem parsing dependency Conflicts
E: Error occurred while processing perl-base (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

---

### Post by dino99 on 2010-06-09
check the synaptic repo: be sure to only use genuine repo (no mixed releases, no ppa) and main server, then :

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a

---

### Post by negatifo on 2010-06-09
I still get the error, after ```
dpkg --configure -a
``` I get this error
dpkg: parse error, in file '/var/lib/dpkg/status' near line 6350 package 'perl-base': `Conflicts' field, missing package name, or garbage where package name expected

---

### Post by negatifo on 2010-06-09
The Solution is
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update
```

---

### Post by negatifo on 2010-06-10
I still can't install/uninstall anything :confused:
I get this error: [B]dpkg: parse error, in file '/var/lib/dpkg/available' near line 6543 package 'perl-base':
 `Conflicts' field, missing package name, or garbage where package name expected[/B]

```
Package: perl-base
Essential: yes
Priority: required
Section: perl
Installed-Size: 4608
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Architecture: i386
Source: perl
Version: 5.10.1-8ubuntu2
Replaces: libperl5.8 (<< 5.8.0-20), libscalar-list-utils-perl, libxsloader-perl, perl (<= 5.10.0-9), perl-modules (<< 5.10.1-1)
Provides: libscalar-list-utils-perl, libxsloader-perl, perl5-base, perlapi-5.10.0, perlapi-5.10.1
Pre-Depends: libc6 (>= 2.11), dpkg (>= 1.14.20)
Suggests: perl
Breaks: doc-base (<< 0.8.16)
Conflicts: autoconf2.13 (<< 2.13-45), libscalar-list-utils-perl (<< 1:1.18-1), libxsloader-perl (<< 0.08-1), (<< 0.8)
Filename: pool/main/p/perl/perl-base_5.10.1-8ubuntu2_i386.deb
Size: 999900
MD5sum: ec0036a4d4175d4d5c80325bdf41d317
Description: minimal Perl system
 Perl is a scripting language used in many system scripts and utilities.
 .
 This package provides a Perl interpreter and the small subset of the
 standard run-time library required to perform basic tasks. For a full
 Perl installation, install "perl" (and its dependencies, "perl-modules"
 and "perl-doc").
Original-Maintainer: Niko Tyni <ntyni@debian.org>
SHA1: 7cc4f78be3e48aa32c3755bd1e432b2c4dcfcd0a
SHA256: 688b751b582f8c58648d716521bf05554909fcc20389085ff8ce5eda5ba520f4
Supported: 5y
Task: minimal
```

---

### Post by plucky on 2010-06-10
```
Conflicts: autoconf2.13 (<< 2.13-45), libscalar-list-utils-perl (<< 1:1.18-1), libxsloader-perl (<< 0.08-1)
```

Is what my **Conflicts** line looks like

```
Conflicts: autoconf2.13 (<< 2.13-45), libscalar-list-utils-perl (<< 1:1.18-1), libxsloader-perl (<< 0.08-1)[color=red], (<< 0.8)[/color]
```
Is what yours looks like.
I would edit the file and remove the part highlighted in red.
Make a backup of the file before editing,just in case you mess up.

Good Luck

---

### Post by negatifo on 2010-06-11
Thanks Man, this solve the problem! (Beer)

---

