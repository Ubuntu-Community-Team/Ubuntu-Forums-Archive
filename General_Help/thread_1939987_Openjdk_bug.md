---
title: "Openjdk bug"
date: 2012-03-12
forum: General Help
---

### Post by jbills on 2012-03-12
For a while now I have been getting the following error when trying to install packages:
```
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 openjdk-6-jre-headless : Depends: openjdk-6-jre-lib (>= 6b23~pre11-0ubuntu1.11.10.2) but 6b23~pre11-0ubuntu1.11.10.1 is installed
E: Unmet dependencies. Try using -f.
```
However when I run the sudo apt-get install -f I get the following result:

```
The following extra packages will be installed:
  openjdk-6-jre-lib
The following packages will be upgraded:
  openjdk-6-jre-lib
1 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
5 not fully installed or removed.
Need to get 0 B/6,090 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 320124 files and directories currently installed.)
Preparing to replace openjdk-6-jre-lib 6b23~pre11-0ubuntu1.11.10.1 (using .../openjdk-6-jre-lib_6b23~pre11-0ubuntu1.11.10.2_all.deb) ...
Unpacking replacement openjdk-6-jre-lib ...
dpkg-deb (subprocess): failed to read on buffer copy for failed to write to pipe in copy: Input/output error
dpkg-deb: error: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/openjdk-6-jre-lib_6b23~pre11-0ubuntu1.11.10.2_all.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/jvm/java-6-openjdk/jre/lib/charsets.jar'
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/openjdk-6-jre-lib_6b23~pre11-0ubuntu1.11.10.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I do not know what the problem is, but I would like fix it soon.

---

### Post by jbills on 2012-03-13
Sorry to double post, but I need to fix this problem. If anyone could help I would appreciate it.

---

### Post by idoitprone on 2012-03-13
I want to get rid of the simpler answers

you might forgot to update those packages

this is pkg bug not openjdk bug
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

