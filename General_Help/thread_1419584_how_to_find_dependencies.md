---
title: "how to find dependencies?"
date: 2010-03-02
forum: General Help
---

### Post by karthick87 on 2010-03-02
Recently i have installed some package from terminal..Now i want to make backup of all those packages for later use..But when i view** /var/cache/apt/archives** all those packages are combined and i dont know the way to seperate the package with its dependencies..If there is a way to find the dependencies of installed package,it might be useful..How to find it?

---

### Post by zvacet on 2010-03-02
```
apt-cache depends package_name
```

---

### Post by karthick87 on 2010-03-03
Similarly how to verify whether the package is installed?For example if i want to check whether squid is installed or not,how do i find that?

---

### Post by elliotn on 2010-03-03
Ait u suppose to type squid in
Terminal.

Not sure

---

### Post by karthick87 on 2010-03-03
I got it,its **sudo aptitude show package_name**

```
karthick@Learners-desktop:~$ **sudo aptitude show perl**
Package: perl
State:** installed**
Automatically installed: no
Version: 5.10.0-19ubuntu1
Priority: important
Section: perl
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 14.0M
Depends: perl-base (= 5.10.0-19ubuntu1), perl-modules (>= 5.10.0-19ubuntu1),
         libc6 (>= 2.4), libdb4.6, libgdbm3
Recommends: netbase
Suggests: perl-doc, libterm-readline-gnu-perl | libterm-readline-perl-perl
Conflicts: libdigest-md5-perl (< 3.07-1), libdigest-sha-perl (< 5.45-1),
           libmime-base64-perl (< 3.07-1), libstorable-perl (< 2.15-1),
           libtime-hires-perl (< 1.86-1), libtime-piece-perl (< 1.12-1),
           perl-doc (< 5.10.0-1)
Replaces: libarchive-tar-perl (<= 1.38-2), libdigest-md5-perl,
          libdigest-sha-perl, libmime-base64-perl, libmodule-corelist-perl (<
          2.14-2), libstorable-perl, libtime-hires-perl, libtime-piece-perl,
          perl-base (< 5.8.8-1), perl-doc (< 5.8.0-1), perl-modules (< 5.8.1-1)
Provides: data-dumper, libdigest-md5-perl, libdigest-sha-perl,
          libmime-base64-perl, libstorable-perl, libtime-hires-perl,
          libtime-piece-perl, perl5
Description: Larry Wall's Practical Extraction and Report Language
 An interpreted scripting language, known among some as "Unix's Swiss Army
 Chainsaw". 
 
 Perl is optimised for scanning arbitrary text files and system administration.
 It has built-in extended regular expression matching and replacement, a
 data-flow mechanism to improve security with setuid scripts and is extensible
 via modules that can interface to C libraries.

```

---

### Post by nothingspecial on 2010-03-03
> **zvacet said:**
> ```
apt-cache depends package_name
```

If you nee to know the dependencies dependencies

```
apt-cache depends --recurse package
```

---

### Post by delectate on 2010-03-03
study,marked

i always do this before:

sudo apt-get install build-dep ***

---

