---
title: "deb package creation problem"
date: 2010-04-28
forum: General Help
---

### Post by Paramita on 2010-04-28
Hi  all,
          I want to build deb packages for two versions of same product that can be installed on the machine simultaneously. The source folder structure for both the packages have a common folder needed by both the versions. So i need to keep the common folder till both the versions are removed from the machine.

          My problem is that i can't install both the versions at the same time, i.e i have to uninstall the installed version and then install the other version. After installing one version, if i try to install another version, an overwrite error comes up.

          Is there any option in dpkg for overwrite? Or is there any way to partially uninstall a deb package?

          Please help!

          Platform: Ubuntu - 9.04

---

### Post by dino99 on 2010-04-28
man dpkg

---

### Post by gmargo on 2010-04-28
Put the common files in a third package, and make the two original packages depend on it.  Many packages are split like this [Try "apt-cache search common | grep -- -common" to see just how many.]

---

### Post by 3rdalbum on 2010-04-28
> **gmargo said:**
> Put the common files in a third package, and make the two original packages depend on it.  Many packages are split like this [Try "apt-cache search common | grep -- -common" to see just how many.]

+1 - this is the correct answer.

---

### Post by debcreate on 2010-07-02
I m new to this and trying to create a single .deb file for a python project binary folder.

i got the following error for dpkg command. could u pls help me out.

dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean
make[1]: Entering directory `/home/ht/Desktop/package/ubuntu/zsync-0.9ubuntu1'
make[1]: *** No rule to make target `clean'.  Stop.
make[1]: Leaving directory `/home/ht/Desktop/package/ubuntu/zsync-0.9ubuntu1'
make: *** [clean] Error 2
dpkg-buildpackage: failure: fakeroot debian/rules clean gave error exit status 2

---

### Post by gmargo on 2010-07-02
What package are you talking about and where did you get the source?  The latest version of zsync is 0.6.1, which is in Lucid.

---

