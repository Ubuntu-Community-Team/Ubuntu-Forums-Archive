---
title: "xulrunner-1.9.2.8 error"
date: 2010-07-31
forum: General Help
---

### Post by bla2000 on 2010-07-31
How do I fix the following:

```
Setting up xulrunner-1.9.2 (1.9.2.8+build1+nobinonly-0ubuntu0.10.04.1) ...
/usr/lib/xulrunner-1.9.2.8/xulrunner-bin: relocation error: /usr/lib/xulrunner-1.9.2.8/libxul.so: symbol SEC_t6veedCertificateTemplate, version NSS_3.4 not defined in file libnss3.so with link time reference
dpkg: error processing xulrunner-1.9.2 (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 xulrunner-1.9.2

```

---

### Post by khelben1979 on 2010-07-31
First we can start off with what [xulrunner]("http://en.wikipedia.org/wiki/Xulrunner") is, check the link.

Then to fix the problem, try this: ```
sudo aptitude install -f
``` or ```
sudo apt-get install -f
``` and report back what happens.

---

### Post by bla2000 on 2010-07-31
Results for:

```
sudo aptitude install -f
```

are:

```
Setting up xulrunner-1.9.2 (1.9.2.8+build1+nobinonly-0ubuntu0.10.04.1) ...
/usr/lib/xulrunner-1.9.2.8/xulrunner-bin: relocation error: /usr/lib/xulrunner-1.9.2.8/libxul.so: symbol SEC_t6veedCertificateTemplate, version NSS_3.4 not defined in file libnss3.so with link time reference
dpkg: error processing xulrunner-1.9.2 (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 xulrunner-1.9.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up xulrunner-1.9.2 (1.9.2.8+build1+nobinonly-0ubuntu0.10.04.1) ...
/usr/lib/xulrunner-1.9.2.8/xulrunner-bin: relocation error: /usr/lib/xulrunner-1.9.2.8/libxul.so: symbol SEC_t6veedCertificateTemplate, version NSS_3.4 not defined in file libnss3.so with link time reference
dpkg: error processing xulrunner-1.9.2 (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 xulrunner-1.9.2
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

```

Results for:

```
sudo apt-get install -f
```

are:

```
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Segmentation fault
Setting up xulrunner-1.9.2 (1.9.2.8+build1+nobinonly-0ubuntu0.10.04.1) ...
/usr/lib/xulrunner-1.9.2.8/xulrunner-bin: relocation error: /usr/lib/xulrunner-1.9.2.8/libxul.so: symbol SEC_t6veedCertificateTemplate, version NSS_3.4 not defined in file libnss3.so with link time reference
dpkg: error processing xulrunner-1.9.2 (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 xulrunner-1.9.2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by bla2000 on 2010-07-31
I also tried:

```
sudo apt-get install --reinstall xulrunner-1.9.2
```

which results in:

```
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Segmentation fault
Setting up xulrunner-1.9.2 (1.9.2.8+build1+nobinonly-0ubuntu0.10.04.1) ...
/usr/lib/xulrunner-1.9.2.8/xulrunner-bin: relocation error: /usr/lib/xulrunner-1.9.2.8/libxul.so: symbol SEC_t6veedCertificateTemplate, version NSS_3.4 not defined in file libnss3.so with link time reference
dpkg: error processing xulrunner-1.9.2 (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 xulrunner-1.9.2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by chrisccoulson on 2010-07-31
No such symbol is exported by NSS on my system. I suspect it is really SEC_SignedCertificateTemplate (same number of characters), and that your install or the downloaded package is corrupted in some way. Try cleaning your apt cache (sudo apt-get clean) and reinstalling the package

---

### Post by bla2000 on 2010-08-01
I tried:

```
sudo apt-get clean
```

as well and the nothing changed.  So I decided to reinstall 10.40 from CD but had problems with the cdrw drive.  During Ubuntu complained about disk read problems.  I tried with 2 different cdrw drives with the same errors.  I also switched 10.04 discs after burning additional copies on anther system.  No luck fixing the hardware issues so I'm taking the system to the recycling centre.  I will purchase a new system later and install Ubuntu on it.

Thanks for helping.

---

### Post by bobook on 2010-09-22
> **bla2000 said:**
> I also tried:

```
sudo apt-get install --reinstall xulrunner-1.9.2
```which results in:

```
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Segmentation fault
Setting up xulrunner-1.9.2 (1.9.2.8+build1+nobinonly-0ubuntu0.10.04.1) ...
/usr/lib/xulrunner-1.9.2.8/xulrunner-bin: relocation error: /usr/lib/xulrunner-1.9.2.8/libxul.so: symbol SEC_t6veedCertificateTemplate, version NSS_3.4 not defined in file libnss3.so with link time reference
dpkg: error processing xulrunner-1.9.2 (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 xulrunner-1.9.2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm having a similar problem. Anyone has other idea?
```

x@ubuntu:/usr/local$ sudo apt-get clean
x@ubuntu:/usr/local$ sudo apt-get install --reinstall xulrunner-1.9.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up xulrunner-1.9.2 (1.9.2.9+build1+nobinonly-0ubuntu0.10.04.1) ...
/usr/lib/xulrunner-1.9.2.9/xulrunner-bin: error while loading shared libraries: libhunspell-1.2.so.0: cannot open shared object file: No such file or directory
dpkg: error processing xulrunner-1.9.2 (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 xulrunner-1.9.2
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by bobook on 2010-09-22
Wow that was a pain but i solved it!

Simply put:
```

sudo apt-get remove --purge  xulrunner-1.9.2
sudo apt-get install -f

```
Cheers!

---

### Post by alexxroche on 2012-05-29
> **bobook said:**
> Wow that was a pain but i solved it!

Simply put:
```

sudo apt-get remove --purge  xulrunner-1.9.2

```Cheers!

Thank you - this also fixed it for me Jim. (Ubuntu 10.04.4 LTS)

---

### Post by oldos2er on 2012-05-29
Old thread closed.

---

