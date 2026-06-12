---
title: "apt-get Broken Packages"
date: 2010-04-30
forum: General Help
---

### Post by sikander3786 on 2010-04-30
Hi. I just installed Ubuntu Lucid and while installed ubuntu-restricted-extras I got some broken packages and now I am unable to remove them.

Any help is appreciated.

```

malik@malik-desktop:~$ sudo dpkg --configure -a
Setting up openjdk-6-jre-headless (6b18-1.8-0ubuntu1) ...
update-alternatives: error: alternative path /usr/lib/jvm/java-6-openjdk/jre/bin/java doesn't exist.
dpkg: error processing openjdk-6-jre-headless (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of openjdk-6-jre:
 openjdk-6-jre depends on openjdk-6-jre-headless (>= 6b18-1.8-0ubuntu1); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing openjdk-6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea-6-jre-cacao:
 icedtea-6-jre-cacao depends on openjdk-6-jre-headless (= 6b18-1.8-0ubuntu1); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing icedtea-6-jre-cacao (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea6-plugin:
 icedtea6-plugin depends on openjdk-6-jre (= 6b18-1.8-0ubuntu1); however:
  Package openjdk-6-jre is not configured yet.
dpkg: error processing icedtea6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ca-certificates-java:
 ca-certificates-java depends on openjdk-6-jre-headless (>= 6b16-1.6.1-2) | java6-runtime-headless; however:
  Package openjdk-6-jre-headless is not configured yet.
  Package java6-runtime-headless is not installed.
  Package openjdk-6-jre-headless which provides java6-runtime-headless is not configured yet.
dpkg: error processing ca-certificates-java (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openjdk-6-jre-headless
 openjdk-6-jre
 icedtea-6-jre-cacao
 icedtea6-plugin
 ca-certificates-java

```

---

### Post by sikander3786 on 2010-04-30
Now whenever I try to install any other package I get the following error.

```

E: /var/cache/apt/archives/ia32-libs_2.7ubuntu25_amd64.deb: short read in buffer_copy (backend dpkg-deb during `./lib32/i486/libcrypto.so.0.9.8')
E: /var/cache/apt/archives/g++-4.4_4.4.3-4ubuntu5_amd64.deb: corrupted filesystem tarfile - corrupted package archive

```

---

### Post by oldos2er on 2010-04-30
```
sudo apt-get clean
``` will clear your cache, afterwards try again to install the packages you want.

If you still have broken packages, run ```
sudo apt-get install -f
```

---

### Post by hvralpha on 2010-05-05
Does not work. Clean command runs, completed doing nothing and it does not fix the problem. Any other ideas how to fix broken packages in Lucid 10.04 x64?

---

### Post by oldos2er on 2010-05-05
System, Administration, Synaptic Package Manager, Edit, Fix broken packages. You also might want to check Settings, Repositories, and make sure all repositories are enabled.

---

### Post by jumping_snake on 2010-05-22
> **oldos2er said:**
> ```
sudo apt-get clean
``` will clear your cache, afterwards try again to install the packages you want.

If you still have broken packages, run ```
sudo apt-get install -f
```

I had the same issue as above after during installing Flash an error occured which left me to do the recommended apt-get clean -> apt-get install -f which made my system re-install ia32-libs_2.7ubuntu25_amd64.deb and then it finished the Adobe Flash install. System's back to working, thanks!!

---

